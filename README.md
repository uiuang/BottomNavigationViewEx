## [中文版点我](/README_ZH.md) ##

## BottomNavigationViewEx ##
An android lib for enhancing BottomNavigationView.

![MIT License](https://img.shields.io/github/license/mashape/apistatus.svg) ![api 9+](https://img.shields.io/badge/API-9%2B-green.svg)


## <a name="donate">Donator</a> ##

| Info | Amount |
|-------|------|
| [Linsong Wang](https://github.com/wanglinsong) | 100$ |


## Features ##

|Method|Description
|---|---|
|enableAnimation|Enable or disable click item animation(text scale and icon move animation in no item shifting mode). Default true.
|enableItemShiftingMode|Enable the shifting mode for each item. It will have a shifting animation for item if true. Otherwise the item text is always shown. Default true when item count > 3.
|enableShiftingMode|Enable the shifting mode for navigation. It will has a shift animation if true. Otherwise all items are the same width. Default true when item count > 3.
|getBottomNavigationItemView|Get private mButton in mMenuView at position
|getBottomNavigationItemViews|Get private mButtons in mMenuView
|getCurrentItem|Get the current checked item position.
|getIconAt|Get icon at position.
|getItemCount|Get item count.
|getItemHeight|Get item height.
|getLargeLabelAt|Get large label at position. Each item has two labels, one is large, the other is small.
|getSmallLabelAt|Get small label at position. Each item has two labels, one is large, the other is small.
|getMenuItemPosition|Get menu item position in menu. Return position if success, -1 otherwise.
|getOnNavigationItemSelectedListener|Get OnNavigationItemSelectedListener.
|setCurrentItem|Set the currently checked item.
|setIconMarginTop|set margin top for icon.
|setIconSize|Set all item ImageView size.
|setIconSizeAt|Set all item ImageView size which is at position.
|setIconsMarginTop|set margin top for all icons.
|setIconTintList| Set item icon tint list.
|setIconVisibility|Change the visibility of an icon.
|setItemBackground| Set background of item.
|setItemHeight|Set menu item height.
|setLargeTextSize|Set all item large TextView size. Each item has two labels, one small and one large. The small one will be shown when item state is normal. The large one will be shown when item is checked.
|setSmallTextSize|Set all item small TextView size. Each item has two labels, one small and one large. The small one will be shown when item state is normal. The large one will be shown when item is checked.
|setTextSize|Set all item large and small TextView size.
|setTextTintList|Set item TextView color.
|setTextVisibility|Change the visibility of text.
|setTypeface|set Typeface for all item TextView.
|setupWithViewPager|This method will link the given ViewPager and this BottomNavigationViewEx together so that changes in one are automatically reflected in the other. This includes scroll state changes and clicks.


## Example ##

**Style**

![](/read_me_images/normal.gif)

![](/read_me_images/no_animation.gif)

![](/read_me_images/no_shifting_mode.gif)

![](/read_me_images/no_item_shifting_mode.gif)

![](/read_me_images/no_text.gif)

![](/read_me_images/no_icon.gif)

![](/read_me_images/no_animation_shifting_mode.gif)

![](/read_me_images/no_animation_item_shifting_mode.gif)

![](/read_me_images/no_animation_shifting_mode_item_shifting_mode.gif)

![](/read_me_images/no_shifting_mode_item_shifting_mode_text.gif)

![](/read_me_images/no_animation_shifting_mode_item_shifting_mode_text.gif)

![](/read_me_images/no_shifting_mode_item_shifting_mode_and_icon.gif)

![](/read_me_images/no_item_shifting_mode_icon.gif)

![](/read_me_images/no_animation_shifting_mode_item_shifting_mode_icon.gif)

**Attention: Something wrong on Android 4.x**

![](/read_me_images/with_padding.jpg)

![](/read_me_images/center_icon_only.jpg)

![](/read_me_images/smaller_text.jpg)

![](/read_me_images/bigger_icon.jpg)

![](/read_me_images/custom_typeface.jpg)

![](/read_me_images/icon_selector_1.jpg) ![](/read_me_images/icon_selector_2.jpg)

![](/read_me_images/icon_margin_top.jpg)

![](/read_me_images/unchecked_first_time.jpg)


**With ViewPager**

![](/read_me_images/with_view_pager.gif)

**Add ViewBadger**

![](/read_me_images/view_badger.gif)

**Center Floating Action Button**

![](/read_me_images/center_fab.jpg)


## Adding to project ##

### Sdk Version ###
`compileSdkVersion` >= 25

### Importing to project(choose one) ###

#### Example for Gradle: ####

Step 1. Add it in your root build.gradle at the end of repositories:
```groovy
allprojects {
	repositories {
		...
		maven { url "https://jitpack.io" }
		maven { url "https://maven.google.com" }
	}
}
```

Step 2. Add the dependency
1. old version support lib is 25 or 26
```groovy
compile 'com.github.ittianyu:BottomNavigationViewEx:1.2.4'
compile "com.android.support:design:26.+"
```
2. new version support lib = 28
```groovy
implementation 'com.github.ittianyu:BottomNavigationViewEx:2.0.4'
implementation "com.android.support:design:28.0.0"
```
3. AndroidX
use new version，and add config into gradle.properties
```
android.useAndroidX=true
android.enableJetifier=true
```

#### Manual: ####

Downloading [BottomNavigationViewEx.java](https://raw.githubusercontent.com/ittianyu/BottomNavigationViewEx/master/widget/src/main/java/com/ittianyu/bottomnavigationviewex/BottomNavigationViewEx.java) and copying it to you project.


## Getting started ##

Adding a custom widget in `xml` :
```xml
<com.ittianyu.bottomnavigationviewex.BottomNavigationViewEx
    android:id="@+id/bnve"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_alignParentBottom="true"
    android:background="@color/colorPrimary"
    app:itemIconTint="@color/selector_item_color"
    app:itemTextColor="@color/selector_item_color"
    app:menu="@menu/menu_navigation_with_view_pager" />
```

Binding view in `Activity`:
```java
BottomNavigationViewEx bnve = (BottomNavigationViewEx) findViewById(R.id.bnve);
```

#### Disable all animations ####
```java
bnve.enableAnimation(false);
bnve.enableShiftingMode(false);
bnve.enableItemShiftingMode(false);
```

#### Custom text and icon size ####
```java
bnve.setIconSize(widthDp, heightDp);
bnve.setTextSize(sp);
```

#### Binding with ViewPager ####
```java
// set adapter
adapter = new VpAdapter(getSupportFragmentManager(), fragments);
bind.vp.setAdapter(adapter);

// binding with ViewPager
bind.bnve.setupWithViewPager(bind.vp);
```

#### Add badge view ####

1. Add badge lib
	```
	compile 'q.rorbin:badgeview:1.1.0'
	```
2. Bind bottom view
	```
    // add badge
    addBadgeAt(2, 1);

    private Badge addBadgeAt(int position, int number) {
        // add badge
        return new QBadgeView(this)
                .setBadgeNumber(number)
                .setGravityOffset(12, 2, true)
                .bindTarget(bind.bnve.getBottomNavigationItemView(position))
                .setOnDragStateChangedListener(new Badge.OnDragStateChangedListener() {
                    @Override
                    public void onDragStateChanged(int dragState, Badge badge, View targetView) {
                        if (Badge.OnDragStateChangedListener.STATE_SUCCEED == dragState)
                            Toast.makeText(BadgeViewActivity.this, R.string.tips_badge_removed, Toast.LENGTH_SHORT).show();
                    }
                });
    }
	```

#### Other usage in BottomNavigationViewEx ####
You can see the demo.

#### Usage in BottomNavigationView ####
Other usage is the same as official `BottomNavigationView`.
You can [click here](https://developer.android.com/reference/android/support/design/widget/BottomNavigationView.html) for detail.

## ProGuard ##

If you are using ProGuard you might need to add the following option:

#### None Android X ####
```
-keep public class android.support.design.widget.BottomNavigationView { *; }
-keep public class android.support.design.internal.BottomNavigationMenuView { *; }
-keep public class android.support.design.internal.BottomNavigationPresenter { *; }
-keep public class android.support.design.internal.BottomNavigationItemView { *; }
```

#### Android X ####
```
-keep public class com.google.android.material.bottomnavigation.BottomNavigationView { *; }
-keep public class com.google.android.material.bottomnavigation.BottomNavigationMenuView { *; }
-keep public class com.google.android.material.bottomnavigation.BottomNavigationPresenter { *; }
-keep public class com.google.android.material.bottomnavigation.BottomNavigationItemView { *; }
```

## References ##

The lib is based on `BottomNavigationView` in `Support Library 25 design`.

I found it was inflexible when I tried the demo. For example, I couldn't change the currently checked item through code. So I wrote a class to extend it to provide some useful methods.

You have no need to worry about stability, because I minimised the modifications through reflection.

## Thanks ##

Thanks to [Adrián Mouly](https://github.com/amouly) | [liaolintao](https://github.com/liaolintao) | [Luong Vo](https://github.com/luongvo).


## License ##

	MIT License
	
	Copyright (c) 2017 ittianyu
	
	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:
	
	The above copyright notice and this permission notice shall be included in all
	copies or substantial portions of the Software.
	
	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
	SOFTWARE.

## Donate ##

**paypal: admin@ittianyu.com**

![](/read_me_images/donate_alipay.png) ![](/read_me_images/donate_wechat.png)

