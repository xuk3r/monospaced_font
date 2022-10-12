# monospaced_font iOS 等宽字体

# 最近看了一下系统的股票软件，发现系统的 .SFUI-Medium 居然是等宽的，研究了一下
![oRPYedNB0H](https://user-images.githubusercontent.com/16160896/195355483-7ce02f8e-8b92-4631-b23a-235bf80b56cd.jpg)

系统用的方法是:
```
+ (UIFont *)monospacedDigitSystemFontOfSize:(CGFloat)fontSize weight:(UIFontWeight)weight API_AVAILABLE(ios(9.0));
```
得到字体：.SFUI-Medium

但是有个问题，我从字宽 0 ~ 100 无法得到 Medium，捣鼓了半天，发现暗藏玄机。
从 -2 ~ 10，依次递增 0.05

* .SFUI-Ultralight <= -0.65
* .SFUI-Thin <= -0.40
* .SFUI-Regular < 0.20
* .SFUI-Medium < 0.25
* .SFUI-Semibold < 0.35
* .SFUI-Bold < 0.60
* .SFUI-Heavy < 0.65
* .SFUI-Black >= 0.65

```
weight -0.700, <UICTFont: 0x7f8a2da0be20> font-family: ".SFUI-Ultralight"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.650, <UICTFont: 0x7f8a4d91c250> font-family: ".SFUI-Ultralight"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.600, <UICTFont: 0x7f8a2da0cda0> font-family: ".SFUI-Thin"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.550, <UICTFont: 0x7f8a6cf2f670> font-family: ".SFUI-Thin"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.500, <UICTFont: 0x7f8a5cf1a460> font-family: ".SFUI-Thin"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.450, <UICTFont: 0x7f8a4cf0fd40> font-family: ".SFUI-Thin"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.400, <UICTFont: 0x7f8a4cf10cc0> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.350, <UICTFont: 0x7f8a5cf1a9b0> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.300, <UICTFont: 0x7f8a2db1fe90> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.250, <UICTFont: 0x7f8a3cf1aa20> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.200, <UICTFont: 0x7f8a3cf1af70> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.150, <UICTFont: 0x7f8a2dc0a3f0> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.100, <UICTFont: 0x7f8a3cf1b4c0> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.050, <UICTFont: 0x7f8a5cf1af00> font-family: ".SFUI-Light"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight -0.000, <UICTFont: 0x7f8a3cf1ba10> font-family: ".SFUI-Regular"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight 0.050, <UICTFont: 0x7f8a4cf11210> font-family: ".SFUI-Regular"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight 0.100, <UICTFont: 0x7f8a4d91c7a0> font-family: ".SFUI-Regular"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight 0.150, <UICTFont: 0x7f8a3cf1bf60> font-family: ".SFUI-Regular"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight 0.200, <UICTFont: 0x7f8a2dc0a940> font-family: ".SFUI-Regular"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight 0.250, <UICTFont: 0x7f8a4d91d830> font-family: ".SFUI-Medium"; font-weight: normal; font-style: normal; font-size: 30.00pt
weight 0.300, <UICTFont: 0x7f8a4d91ea30> font-family: ".SFUI-Semibold"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.350, <UICTFont: 0x7f8a3cf1c4b0> font-family: ".SFUI-Semibold"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.400, <UICTFont: 0x7f8a3cf1d400> font-family: ".SFUI-Bold"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.450, <UICTFont: 0x7f8a3cf1d950> font-family: ".SFUI-Bold"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.500, <UICTFont: 0x7f8a3cf1dea0> font-family: ".SFUI-Bold"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.550, <UICTFont: 0x7f8a3cf1e3f0> font-family: ".SFUI-Bold"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.600, <UICTFont: 0x7f8a3cf1f370> font-family: ".SFUI-Heavy"; font-weight: bold; font-style: normal; font-size: 30.00pt
weight 0.650, <UICTFont: 0x7f8a3cf202f0> font-family: ".SFUI-Black"; font-weight: bold; font-style: normal; font-size: 30.00pt
```

有需要用到等宽字体的同学可以参考一下。
