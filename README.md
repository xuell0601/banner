第一步：添加依赖
compile 'com.youth.banner:banner:1.4.2'  //指定版本

第二步：在布局文件中：
<com.youth.banner.Banner
    android:id="@+id/banner"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

</com.youth.banner.Banner>

<!--<android.support.v4.view.ViewPager-->
 <!--android:id="@+id/vp_home"-->
 <!--android:layout_width="match_parent"-->
 <!--android:layout_height="match_parent">-->

<!--</android.support.v4.view.ViewPager>-->

<!--<com.viewpagerindicator.CirclePageIndicator-->
 <!--android:id="@+id/cp_home"-->
 <!--android:layout_width="match_parent"-->
 <!--android:layout_height="15dp"-->
 <!--android:layout_gravity="bottom|center_horizontal"-->
 <!--android:layout_marginBottom="5dp" />-->

第三步：代码中实现：
//设置banner样式
banner.setBannerStyle(BannerConfig.CIRCLE_INDICATOR_TITLE);
//设置图片加载器
banner.setImageLoader(new GlideImageLoader());
//设置图片url集合:imageUrl
List<String> imageUrl = new ArrayList<String>(images.size());
for (int i = 0; i < images.size(); i++) {
    imageUrl.add(images.get(i).IMAURL);
    Log.e("TAG", "url = " + images.get(i).IMAURL);
}
banner.setImages(imageUrl);
//设置banner动画效果
banner.setBannerAnimation(Transformer.DepthPage);
//设置标题集合（当banner样式有显示title时）
String[] titles = new String[]{"分享返学费1111元", "人脉总动员", "想不到你是这样的APP", "11月兑物节"};
banner.setBannerTitles(Arrays.asList(titles));
//设置自动轮播，默认为true
banner.isAutoPlay(true);
//设置轮播时间
banner.setDelayTime(1500);
//设置指示器位置（当banner模式中有指示器时）
banner.setIndicatorGravity(BannerConfig.RIGHT);
//banner设置方法全部调用完毕时最后调用
banner.start();

其中，
public class GlideImageLoader extends ImageLoader {
    @Override
    public void displayImage(Context context, Object path, ImageView imageView) {

        //Picasso 加载图片简单用法
        Picasso.with(context).load((String) path).into(imageView);

    }
}
