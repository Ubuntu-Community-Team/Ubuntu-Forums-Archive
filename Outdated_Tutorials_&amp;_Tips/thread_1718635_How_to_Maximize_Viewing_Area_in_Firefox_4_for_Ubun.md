---
title: "How to Maximize Viewing Area in Firefox 4 for Ubuntu"
date: 2011-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by SenorFusion on 2011-03-31
Hey All,


I am a complete Linux newbie (been running MM for about a month now). I like to offer something useful when I join forums instead of begging for help with my first post, so I put together a tutorial for that has been a very nice fix for me.

I'm sure this is a super newbie tutorial for most, but it's my first.

If you are like me you spend the majority of your time on the PC (especially the laptop) within your Browser. I'm also crazy about screen real estate. In literally makes me cringe to see people in the coffeeshop with half a dozen "toolbars" on their browser and lose half their screen space for the area they spend 90% of their time staring at so I set out to maximize my viewing area for Firefox 4.

This achieved with:

Ubuntu 10.10 MM using Ambience
Firefox 4
CompizConfig Settings Manager
gconf-editor


**1. Remove Firefox Title Bar**

In Firefox 4, in my opinion, the Titlebar is an utterly useless waste of screenspace. It's almost the exact same color as the Menu Bar and only holds the Max/Min/Close Buttons

To Remove the Firefox titlebar, and ONLY the Firefox title bar:

System > Preferences > CompizConfig Settings Manager > Window Decoration > 

change Decoration Windows to: any & !(class=Firefox & state=maxvert)

This way all of your other windows will keep their Title Bar and Max/Min/Close Buttons

Yes this means when working with the firefox window you will have to use keyboard shortcuts to Close/Move/Resize OR do what I do and simply right click on the window in your panel to Close/Move/Resize

credit to: Flynn555 for this [http://ubuntuforums.org/showthread.php?t=1064144](http://ubuntuforums.org/showthread.php?t=1064144)

**2. Tabs On Top**

Firefox > Edit > Preferences > Tabs On Top 

This moves Firefox Tabs above the nav bar, and after we hide the Menu Bar the tabs will be flush with the top of your screen, similar to chrome.

**3. Hide Menu Bar**

Firefox > Edit > Preferences > Uncheck Menu Bar

With what I think is the best UI improvement in FF 4 - the Menu Bar now folds up into one single button and sits beside your tabs.

**4. Combine Bookmarks ToolBar and Nav Bar**

If you don't use Bookmark Buttons you can ignore this step.

I like to keep Bookmark buttons of my most visited sites easily available (Facebook, Gmail, Google Reader, etc) However, I hate how much space vertical real estate the bookmarks toolbar takes up, so I combine it with the Nav bar.

Firefox > Preferences > Check Bookmarks Toolbar if not already

From here on down, when I mention "Firefox" it refers to the Firefox Button now in the top left of your screen.

Then

Firefox > Preferences > Toolbar Layout > Drag the Bookmarks Toolbar Buttons between your Nav Buttons and Nav Bar on the line above.

Tip: To minimize the space these buttons take up, I bookmark my most used sites, but leave the bookmark name field blank. This way in the toolbar on the Icon for the bookmark shows up.

**5. Disable Bookmark Buttons Toolbar**

Now you have a blank bookmarks bar taking up valuable screenspace, so we disable it, but don't lose our bookmark buttons.

Firefox > Preferences > Uncheck Bookmarks Toolbar

**6. Auto Hide Panel**

This is a personal preference, and outside the scope of this tutorial, but since Firefox 4 made the Status bar optional, I autohide the panel so FF extends all the way to the bottom of my screen.

**7. Always Show Tabs Preference**

To further maximize screen space you can choose

Firefox > Preferences > Preferences > Uncheck Always show the Tab Bar

If you are only working in 1 Tab, this tutorial has slimmed down your vertical screen space lost too only a single bar.

**Note: After doing this, you will only be able to access the Firefox button (i.e. menu items) by opening a second tab and forcing firefox to show the Tab Bar where the menu button now resides.

To me this is a small issue and worth the tradeoff.


Following these steps I am able to run Firefox using only 32 of 900 vertical pixels with only 1 tab, and 57 out of 900 vertical pixels with multiple tabs open.

That's only 3.5% and 6.3% of my vertical screen space respectively, and all the rest available for my browsing pleasure.

I've attached screenshots of this beautifully clean firefox browsing setup with no tabs and multiple tabs - All functionality and no wasted space.

If you have questions or ways to improve the setup let me know,

Thanks

---

