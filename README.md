### HorizontalRefreshLayout
a android layout widget for horizontal drag refresh action (viewpager or recyclerview or horizontal Scrollview)
-----
![](https://github.com/29995270/HorizontalRefreshLayout/blob/master/art.gif "viewpager")
<br>
how to use
-----
```xml
    <com.wq.freeze.horizontalrefreshlayout.lib.HorizontalRefreshLayout
        android:id="@+id/refresh"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="@android:color/white">
        <android.support.v4.view.ViewPager
            android:id="@+id/vp"
            android:layout_width="match_parent"
            android:layout_height="300dp"/>
    </com.wq.freeze.horizontalrefreshlayout.lib.HorizontalRefreshLayout>
```

```java
    refreshLayout.setRefreshMode(HorizontalRefreshLayout.MODE_ABOVE);
    //MODE_ABOVE: RefreshHeader above of refreshable view
    //MODE_UNDER: RefreshHeader under the refreshable view
    //MODE_UNDER_FOLLOW_DRAG: RefreshHeader under the refreshable view and follow drag action

    //define your RefreshHeader
    refreshLayout.setRefreshHeader(new MaterialRefreshHeader(HorizontalRefreshLayout.START),
                    HorizontalRefreshLayout.START);
    refreshLayout.setRefreshHeader(new MaterialRefreshHeader(HorizontalRefreshLayout.END),
            HorizontalRefreshLayout.END);

    refreshLayout.setRefreshCallback(this);
        
    @Override
    public void onLeftRefreshing() {
        refreshLayout.postDelayed(new Runnable() {
            @Override
            public void run() {
                adapter.onRefresh();
                refreshLayout.onRefreshComplete();
            }
        }, 1000);
    }

    @Override
    public void onRightRefreshing() {
        refreshLayout.postDelayed(new Runnable() {
            @Override
            public void run() {
                adapter.onLoadMore();
                refreshLayout.onRefreshComplete();
            }
        }, 1000);
    }
```
