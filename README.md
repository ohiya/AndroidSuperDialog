# AndroidSuperDialog
   基于`DialogFragment`封装，支持自定义边框圆角、背景透明度、字体大小与色值等。
   列表选择框可以接收`List`与`Arrays`的数据源，详细见`demo`。
   初衷是掌握知识点，此库不一定适合你的产品整体风格，当然能够适合你的项目最好不过，有建议和不足之处欢迎骚扰。
# 知识点
  全代码创建`shape`、`selector`、`Layout`，三大`Layout`不用多讲，肯定都会的，主要是`Shape`所使用类如下：
  * `shape`对应`ShapeDrawable`、`RoundRectShape`
  * `selector`对应`StateListDrawable`

#效果图
<img src="preview/superDialog_01.png" width="240px"/>

<img src="preview/superDialog_02.png" width="240px"/>

<img src="preview/superDialog_03.png" width="240px"/>
# 引入

```xml
 compile 'com.mylhyl:superDialog:1.0.2'
```

#使用
简单的对话框

```java
                new SuperDialog.Builder(this).setRadius(10)
                        .setAlpha(0.5f)
                        .setTitle("标题").setMessage("可以看到？")
                        .setPositiveButton("确定", new SuperDialog.OnClickPositiveListener() {
                            @Override
                            public void onClick(View v) {
                                Toast.makeText(v.getContext(), "点了确定", Toast.LENGTH_LONG).show();
                            }
                        }).build();
```

选择对话框

```java
                //final String[] strings = {"拍照", "从相册选择", "小视频"};
                List<People> list = new ArrayList<>();
                list.add(new People(1,"拍照"));
                list.add(new People(2,"从相册选择"));
                list.add(new People(3,"小视频"));
                new SuperDialog.Builder(this)
                        //.setAlpha(0.5f)
                        //.setGravity(Gravity.CENTER)
                        //.setTitle("上传头像", ColorRes.negativeButton)
                        .setCanceledOnTouchOutside(false)
                        .setItems(list, new SuperDialog.OnItemClickListener() {
                            @Override
                            public void onItemClick(int position) {
                                Toast.makeText(MainActivity.this, strings[position], Toast.LENGTH_LONG).show();
                            }
                        })
                        .setNegativeButton("取消", null)
                        .build();
```

#说明
	* 此库自动将px转换百分比，由于 Dialog 布局一般只有微调，暂时只支持textSize，height，padding
	* 默认字体大小;Title、message、button、padding 的px在设计稿为 1080 * 1920 的尺寸
	* 所以使用时设计稿尺寸一定是1080 * 1920
QQ交流群:435173211

#感谢
[AutoLayout-Android](https://github.com/DTHeaven/AutoLayout-Android)

# 版本

> 1.0.2 增加背景方法`setBackgroundColor`
