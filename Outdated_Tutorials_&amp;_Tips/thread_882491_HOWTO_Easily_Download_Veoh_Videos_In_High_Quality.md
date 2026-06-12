---
title: "HOWTO Easily Download Veoh Videos In High Quality"
date: 2008-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by ntowakbh on 2008-08-07
[CENTER][SIZE="6"]Purpose[/SIZE][/CENTER]
On Linux, from what I've found, there is no easy way to download high quality videos from Veoh, by default.  This will give a user two options that should make it much easier, and possible.  One by adding a bookmark to Firefox that would download the video when clicked, or by adding a link to the page of the video.  This should let you get the high quality videos, not just the low quality FLVs.

[CENTER][SIZE="6"]What is needed[/SIZE][/CENTER]
You will need to download the zip file of [[COLOR="Blue"]VeohProxy[/COLOR]](http://code.google.com/p/veohproxy/) to your home directory.  Here is a [[COLOR="Blue"]direct download link for VeohProxy[/COLOR]](http://veohproxy.googlecode.com/files/VeohProxy-1.4.zip), if you don't want to follow the external link for the download.

Firefox for the bookmark, currently I don't know for sure how to get the bookmark to work on Opera -- if someone can get the bookmark trick to work on Opera, message me, and I will update the tutorial.

Firefox, with the [[COLOR="Blue"]Greasemonkey[/COLOR]](https://addons.mozilla.org/en-US/firefox/addon/748) extension, if you want to put the download link directly on the page.  [The way I get the link working, is by using a user script that I made.]

[CENTER][SIZE="6"]Steps[/SIZE][/CENTER]

**[SIZE="5"]First[/SIZE] -- unzip the files.** - Move the .zip file to the directory that you want to extract the VeohProxy folder to, then navigate to that folder with nautilus, right click the file, and hit extract.  **_Make note of the directory that it is extracted to!_** On mine, I extracted the .zip file inside of my */home/[username]/bin* folder, so the resulting folder for me is *_/home/[username]/bin/VeohProxy-1.4_* 

**[SIZE="5"]Second[/SIZE] -- run VeohProxy on startup.** - Add VeohProxy.py to your startup programs.  In GNOME, go to the menu, and then "System->Preferences->Sessions"  Then click "Add." The window that pops up should look something like this - 
[img]http://img361.imageshack.us/img361/6246/addstartuphr6.jpg[/img]

For the name, use "VeohProxy."  For the command, use _python _ and then the folder that was extracted from the zip file, and then add _VeohProxy.py_.  For example, my command is -- _python /home/ntowakhb/bin/VeohProxy-1.4/VeohProxy.py_

Once you've done that, restart your computer, or log out and back in again, either one works.  

**[SIZE="5"]Third[/SIZE] -- Making the Bookmark**
Open Firefox, and right click the bookmark bar, and select "New Bookmark..."  You should get a pop up that looks something like this --
[img]http://img507.imageshack.us/img507/5373/bookmarkol3.jpg[/img]
Name the bookmark whatever you want, but for the location, use -- _javascript:document.location="http://ntowa.com/scripts/vproxyredir.html?video="+escape(window.location);_

The webpage it redirects to, is a page that contains javascript that I wrote that should work specifically for this, if you have VeohProxy.

Here is the source code of the page for those who want it [if anyone would like to mirror the page, I would be happy to add their mirror to the tutorial in addition to my own] --
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
	<head>
		<title>Redirecting...</title>
		<script type="text/javascript">
		<!--
		function readgetvar(name)
		{
			var locser = location.search;
			var searchquar = name + "=";
			
			if(locser.search(searchquar) == -1)
			{
				return "Could not detect get variable.";
			}
			
			else
			{
				var starter = locser.search(searchquar) +searchquar.length;
				var blah = new Array();
				var count=0;
				
				for(var i=starter;i<locser.length && locser.charAt(i) != "&" && locser.charAt(i) != "#";i++)
				{
					blah[count]=locser.charAt(i);
					count++;
					var result = blah.join("");
				}
				return unescape(result);
			}
		}
		
		var vurl = readgetvar("video");
		var vproxy = "http://127.0.0.1:64653/";
		var searchquar = "/videos/";
		var starter = vurl.search(searchquar) + searchquar.length;
		var blah = new Array();
		var count=0;
						
		for(var i=starter;i<vurl.length && vurl.charAt(i) != "&" && vurl.charAt(i) != "#" && vurl.charAt(i) != "?";i++)
		{
			blah[count]=vurl.charAt(i);
			count++;
			var video = blah.join("");
		}
		document.location = vproxy+video;
		//-->
		</script>
	</head>
	<body>
		
	</body>
</html>

```
Now, simply click the bookmark while watching a video on Veoh, and you should get a download of the high quality video.

**[SIZE="5"]Fourth[/SIZE] -- Making the link on Veoh videos.**
Here is a screenshot of what the link will look like, I outlined the link in red on the screenshot to show you where it should appear --
[[COLOR="Blue"]Click here for screenshot[/COLOR]](http://img112.imageshack.us/img112/1362/screengu9.jpg)(way too big for the forum)

As I mentioned earlier, you will need to have installed the [[COLOR="Blue"]Greasemonkey[/COLOR]](https://addons.mozilla.org/en-US/firefox/addon/748) extension for Firefox.  Once you have done that, just visit this link to a Greasemonkey script I made to [[COLOR="Blue"]add the video download link[/COLOR]](http://ntowa.com/scripts/add_video_download_link_.user.js).  It should popup that it is a greasemonkey script and ask you about installing it.  Just click install.

Again, here is the source of the script for those that want it --
```

// ==UserScript==
// @name           Add video download link for linux to veoh.
// @namespace      http://ntowa.com
// @description    Requires that you have veoh proxy installed and running.
// @include        http://www.veoh.com/videos/*
// @include        http://veoh.com/videos/*
// ==/UserScript==

var dlopt = document.getElementById('downloadOptions');

var link = '<a href="javascript:document.location=\'http://ntowa.com/scripts/vproxyredir.html?video=\'+escape(window.location);">Download on Linux</a>';

dlopt.innerHTML = link; 

```
Now, simply click the link while watching a video, and you should get a download for the high quality video!

----

I hope this tutorial was able to help someone.

---

