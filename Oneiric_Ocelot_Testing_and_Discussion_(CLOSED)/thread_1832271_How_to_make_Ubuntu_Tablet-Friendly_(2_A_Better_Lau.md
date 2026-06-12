---
title: "How to make Ubuntu Tablet-Friendly (2: A Better Launcher)"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ErkDemon on 2011-08-24
The Ubuntu 11.04 Unity program launcher wasn't particularly great. The *idea* of an edge-positioned finger-friendly launcher strip along one edge of the screen was good, but the implementation was too limited. 

**Docking:** 
A credible launcher strip should be dockable to any edge, left, right, top, bottom. That's an ability that we've expected on third-party docker strips since the days of the Atari ST, and there's no obvious reason why a 2011 operating system addon should have less functionality than one from 1985. This flexibility is *_more_* important for tablets than desktops, because users may be holding the device in either hand, in any orientation. 

I understand the Canonical argument that having a nice chunky strip locked to the screen;s side probably makes for the most efficient use of space on a small wide-screen-format device held in landscape mode (say, 1024*600, or 800*400), but that same argument would say that that side-strip then represents the /worst/ possible use of screen space if the wide-screen tablet's being held in portrait mode. So if you accept Canonical's design argument that usable screen area overrides other considerations, you have to accept that for a tablet held in portrait mode, the existing left-bar is a bit of a design failure. And people do tend to hold their tablets in portrait mode rather a lot.

Now, okay, I accept that there's a potential usability problem in allowing the strip to be dragged to new locations by a user with fat fingers, especially if the strip has tiny borders to minimise wasted space. And without being able to right-click on the strip or use a modifier key, it's difficult to know where to put the strip's "settings" functions. But the suggestions in Part One go some way to solving the modifier-key issues, and the others can be addressed by adding a "page" control pad…  

**Launchstrip Paging: **
The current program launcher isn't good if you have more than about four or five apps that you use, because the rest tend to get squished into a nasty compacted pile at the bottom of the strip, and you have to hover your mouse over the pile and wait for the unpacking animation to happen , and … its horribly slow. Quite apart from the fact that, if you're not using a mouse or wacom tablet, you probably don't have the hover function anyway … 
So, if you're dedicating a precious piece of of your launcher's screenspace to the compacted pile of additional icons, why not replace it with a simple page button at the top of the strip, that lets you click through pages of additional apps? A "page" button could also let you step through to other strip pages with additional functions, like the "modifier pads" page in Part One, turning the launcher strip into a general-purpose helper strip rather than just a crude app launcher. The paging button would also be the convenient piece of strip that you could drag to move the whole strip to another screen edge, and it'd be the area that you press-and-hold to get the popup menu that lets you jump the strip to different edges or launch a configuration applet. Or maybe press-and-hold could make the strip expand to multiple columns, to show all the apps at once, until you poke one of their icons, or poke the paging button a second time to drop back to a single column. If you want to launch an app, it's nice for the existing screen to stay at last partly visible (for continuity), but you don't need to see all of it. Even if the launcher briefly covers half the screen when you're making your selection, that's okay. 

**Additional launchstrip functions:**
Once you have a paging, multifunction launchstrip, you can use it for other things. 

Any wacky new ideas that you have for user-interface additions can be trialled as additional launchstrip pages. You can have buttons that launch boilerplate text, a pop-out configurable ASCII keyboard, a new clipboard manager, website bookmarking with launchstrip thumbnails, google map locations, main contact lists with thumbnails, all sorts of things. Page the strip to the "people" page, click a face, and send them an message, view their last email, look at their twitter feed. If you're browsing the web, you'll probably page the strip to its bookmarking functions page, if you're reading an ebook, you'd probably cycle through to the page that gives the strip a set of pads optimised for book-reading (back/forward/pageup/pagedown/home/store-or-recall-current-position). If you want function keys, you can page through to the function-key strip. If you want numerical input, you page to the number strip, with format conversion, popup keypad and popout calculator functions. If you're editing text, page to the strip that has cursor keys and dedicated buttons for cut/copy/paste/undo/save, which launch Ctrl-X / Ctrl-C / Ctrl-V / Ctrl-Z / Ctrl-S .

The strip could become a general-purpose helper that's always just a finger-jab away at the edge of your screen, with whatever page of functions you currently find most useful. It could be truly great. So some of the design philosophy behind the 11.04 Unity launcher was actually okay. It just needed to be a lot more ambitious. 

**Customisation:**
There are some functions, like the sticky-pad features, that might need OS-level interfacing. For a lot of others, advanced users could "roll their own". Strip "pages" could be written as HTML5 fragments, as individual HTML files (so that you could add your own page by saving a new HTML file to the relevant folder without risking screwing up the existing ones), or as multi-page files separated by HTML5 section tags. Individual pads or buttons would probably be "list" items inside an HTML5 "menu" block. 
The code that runs the strip wouldn't need (or want) to be a fully-fledged webbrowser, it could just scan a text file to find the first <menu></menu> block and then pick out the limited set of commands that it understands, like list item, image, hover text, link, and maybe background image and colour. You'd probably not want to implement anything fancy like javascript for security reasons. The ability to launch keycodes or sequences from a button would be useful, though.
 
If anyone really hated the strip as it was configured in the default OS release, then instead of complaining, they could go away and write their own strip pages and then share them as HTML files. Any little specialist group could write button strips or bookmarks for their own purposes, so if someone decided that there was a need for a custom strip with an arbitrary selection of keycodes displayed as Playstation controller symbols, or unicode symbols (like the copyright symbol or non-western characters), they could knock up a quick strip themselves using a webpage editor or notepad. If the strip code only reads the contents of the first <menu></menu> tag and ignores everything else on the page, then people couldn publish and share their strips online as webpages with additional comments and documentation right on the page alongside the strip. The user could save the page to a system folder and have the buttons or pads then appear as one of their strips, with the additional webpage material being ignored by the OS when it scanned the file for usable button info.   

This could be genuinely exciting, it wouldn't take that much work, and instead of locking people out of the ability to decide how their desktop looks and works, it could empower them. And as a bonus, it'd mean that the number of people developing user-interface strips for the Ubuntu desktop would go through the roof.

---

### Post by jbicha on 2011-08-24
Failure of the launcher to orient itself smartly when the display switches to portrait mode is a bug and is not the intentional behavior. If the launcher always does the Right Thing, then there isn't a need to configure it.

Your pages thing is very weekly implemented by workspaces. Obviously, you're pulling a lot of OS X Lion design into it. Workspaces in Unity as yet don't work very well so perhaps that will get looked at in the future. And Unity does have its lenses thing which is a search-driven "strip" interface.

---

