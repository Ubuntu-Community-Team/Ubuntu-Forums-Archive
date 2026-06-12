---
title: "Firefox Font Display layout in Firefox 4 &amp; 5"
date: 2011-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by excaliber27 on 2011-06-22
For years I've been been using the same userChrome.css for my custom font layout in Firefox. 
However, Firefox 4 doesn't use a userChrome.css file to customize the font layout.

NOW WHAT?

Searching Google, I found the [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/stylish/") add-on for Firefox 4 & 5 and it worked.

After you install Stylish, here's what you have to: 
1. Go to Tools, Add-on's
2. Click Preferences beside Stylish
3. Select "Write new style" and paste the attached css info below.
4. Save it (under whatever name you wish and add tags if desired).
5. Done 

Everything should now look as it does in windows.

(PS. Make sure to [FONT="*Courier New"]sudo apt-get install msttcorefonts*[/FONT])


[I]/*
 * Edit this file and copy it as userChrome.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */


/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*
 * Make menu items in particular 15 pt instead of the default size:
 */
 * menubar > menu,menupopup > menuitem > menupopup >*
   menubar, menubutton, menulist, menu, menuitem {
   font-size: 3mm !important
 }
 *
/* Set font for tabs' text */
.tab-text
{
font-size: 8.5pt !important;
}
/* change fontsize on text with icons, navigation, personal bookmarks,
     does not affect the menu bar */
.toolbarbutton-text {-moz-appearance: none !important; 
     font-size: 8.5pt !important;}

/ * Give the Location (URL) Bar a fixed-width font
 *
 * #urlbar {
 *    font-family: monospace !important;
 * }
 */

/*
 * Eliminate the throbber and its annoying movement:
 *
 #throbber-box {
 display: none !important;
 }
 */

/*
 * For more examples see [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html)
 */

[/I]

---

