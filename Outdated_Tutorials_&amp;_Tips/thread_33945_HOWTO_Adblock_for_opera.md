---
title: "HOWTO: Adblock for opera"
date: 2005-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Lars A E on 2005-05-12
Hi!

This howto is based on this [guide](http://nontroppo.org/wiki/OperaLuaAdblock) and some google search needed to fill in the holes.
Note! I've only tested this with Opera 8.0

[list=1]
[*]Install lua 
```
sudo apt-get install lua50
``` 


[*]Create an empty css-file (e.g. adblock.css) somewhere in your filesystem. I'll assume ~/.opera/adblock.css in the rest of this howto.



[*]Create a lua script somewhere in your filesystem. Again I'll assume ~/.opera/adblock.lua. The script should contain the following:
```
if table.getn(arg)<1 then os.exit() end
BLOCK_CSS_FILE="~/.opera/adblock.css"

cssFile=io.open(BLOCK_CSS_FILE)
if cssFile then
  cssStr=cssFile:read("*a") or ""
  cssFile:close()
end

cssFile=io.open(BLOCK_CSS_FILE,"w")
if table.getn(arg)==1 then cssFile:write('img[src="'..arg[1]..'"]')
elseif table.getn(arg)==2 then cssFile:write(arg[2]..'"'..arg[1]..'"]')
elseif table.getn(arg)==3 then cssFile:write(arg[2]..'['..arg[3]..'='..'"'..arg[1]..'"]')
elseif table.getn(arg)==4 then cssFile:write(arg[2]..'['..arg[3]..arg[4]..'"'..arg[1]..'"]')
end
if (cssStr=="\n") or (cssStr=="") then cssFile:write('\n{display:none !important;}')
     else cssFile:write(',\n'..cssStr) end
cssFile:close()
```
Remember to change the path in the 2nd line if necessary.



[*]Create a new menu command.
In opera, goto Tools>Preferences>Advanced>Toolbars and click the lower **duplicate** button. This should create a new .ini-file in your ~/.opera/menu/ directory. Open this file and paste the following line at the end of these two sections [Image Link Popup Menu] and [Image Popup Menu].
```
Item, "Destroy image" = Copy image address & Execute program, "lua", "~/.opera/adblock.lua %c" & Select user CSS file,1 & Deselect user CSS file, 1 & Select user CSS file,1 & Deselect user CSS file, 1

```
The end result should look something like this:
```

<other stuff>

[Image Link Popup Menu]
Item, 67389=Open link
Item, 53018=Open link in new page
Item, 53019=Open link in background page
--------------------1
Item, 54020=Open link in new window
Item, 67633=Open link in background window
--------------------2
Item, 70463=Add link to bookmarks
Item, 50216=Copy link
Item, 50761=Save link
Item, 67350=Download url
--------------------3
Item, 67651=Open image
Item, 70486=Load image
Item, 50419=Copy image address
--------------------4
Item, 50262=Save image
Item, 70466=Copy image
Platform Windows-Mac-QNX, Item, 70467,=Use image as desktop background
--------------------5
Item, 56064=Show image properties
--------------------6
Item, "Destroy image" = Copy image address & Execute program, "lua", "~/.opera/adblock.lua %c" & Select user CSS file,1 & Deselect user CSS file, 1 & Select user CSS file,1 & Deselect user CSS file, 1

<other stuff>

[Image Popup Menu]
Item, 67651=Open image
Item, 70486=Load image
Item, 50419=Copy image address
--------------------1
Item, 50262=Save image
Item, 70466=Copy image
Platform Windows-Mac-QNX, Item, 70467=Use image as desktop background
--------------------2
Item, 56064=Show image properties
--------------------3
Item, "Destroy image" = Copy image address & Execute program, "lua", "~/.opera/adblock.lua %c" & Select user CSS file,1 & Deselect user CSS file, 1 & Select user CSS file,1 & Deselect user CSS file, 1

<other stuff>

```



[*]Enable user css files.
In opera, goto Tools>Preferences>Advanced>Content. Here, click on the **style options** button. Enable **My style sheet** under **Author mode** and set the path to your style sheet in the text box. In my case:
```
~/.opera/adblock.css
```
[/list]


Now you can remove ads by right-clicking them and choosing **Destroy image** in the menu. The URL to the ad is stored in your stylesheet by the lua script for future blocking of the same ad.

---

### Post by Xian on 2005-05-12
Very nice. I set this up as written and it works beautifully.

Thanks.   [img]http://ubuntuforums.org/images/smilies/eusa_dance.gif[/img]

---

### Post by raven on 2005-05-17
HI, I followed your instruction by the letter couple of times
but it did not work for me
I have the right click context menu "Destroy Image"
when I click on an add or an image, it just 
freezes for a 2 sec and that's it
I don't have anything written in adblock.css
any Idea ???
thanx

---

### Post by Lars A E on 2005-05-17
A few things you can check:
1. Do you have lua set up correctly. Try running the command
```
lua
``` 
2. Do you have the right permissions set for adblock.css. If you created the file as root or using sudo, your user will not have write permission.

---

### Post by raven on 2005-05-17
thanx for the fast reply
lua command will give me
"Lua 5.0.2  Copyright (C) 1994-2004 Tecgraf, PUC-Rio"
I installed it with synaptic
I created the files with my user "NO SUDO"
to create the files I just did the right click > create empty file >
rename it to adblock.css, the same for adblock.lua
in the folder that you mention ~/.opera/
I checked permissions on the 2 files and the file that
opera will create when I duplicate the menu
name of file "standard_menu (1).ini" all have my user as owner
with the right permissions
I did not change this file name "standard_menu (1).ini"
and it is the only file in the menu folder,

the only thing I don't understand
when I modify any file of those 3, a new file will be created with
the same name ex: adblock.css another file is created adblock.css~
I thought this is like "office when you have a .doc open"
you will have a replica woking on, but when I close the editor this file remains ?
anyway I tried by leaving this file, or by deleting it same issue.

sorry, maybe too much info
but I rather gives all steps that I did
so you will understand better what the issue.

---

### Post by raven on 2005-05-17
got it working after a bit of experimenting
the mistake was in the code "~/.opera/adblock.lua %c"
I had to put the complete path "/home/usename/.opera/adblock.lua %c"
thanx it works perfectly now

---

### Post by Lars A E on 2005-05-18
I'm glad it worked out!
The *.*~ files are created by gedit whenever you save a file. It's a copy of the last saved version. This feature can be turned off in edit>preferences>editor.

---

### Post by Juippisi on 2005-06-01
Wow, thanks for this howto. It really works and now I can use Opera again. I used Firefox just because of the adblock-feature.
By the way, where those blocked image (URL's?) goes, I wan't to try importing my Firefoxes adblock-list to Opera :). 

This howto and [this](http://www.ubuntuforums.org/showthread.php?t=36070&highlight=opera+adblock) thread just makes Opera the best.

---

### Post by Lars A E on 2005-06-01
[QUOTE=Juippisi]Wow, thanks for this howto. It really works and now I can use Opera again. I used Firefox just because of the adblock-feature.
By the way, where those blocked image (URL's?) goes, I wan't to try importing my Firefoxes adblock-list to Opera :). 

This howto and [this](http://www.ubuntuforums.org/showthread.php?t=36070&highlight=opera+adblock) thread just makes Opera the best.[/QUOTE]
 The URL's are added to the adblock.css file.

---

### Post by pdk001 on 2005-06-01
thanks for tip

---

### Post by dakira on 2005-07-04
Hi, nice guide!

Has an improvement to your guide I would recommend not starting with an empty adblock.css but with an intelligently preconfigured one.

The first choice is this:
[http://members.chello.nl/b.kroonspecker/opera/styles/user/AdBlocker.css](http://members.chello.nl/b.kroonspecker/opera/styles/user/AdBlocker.css)

The above AdBlocker is updated frequently but you don't really need to update.. it works good as it is and for the rest you can use the right-click destroy image. There is just one problem with the above file. That is "section 2" (Webbugs, useless spacers, and micro-ad trackers). It removes elements which are sometimes necessary for page layout so it renders some pages ugly. Just remove that section and you're good to go.

cheers
dakira

---

### Post by Juippisi on 2005-07-19
Wow, thanks Dakira!

---

### Post by dakira on 2005-10-19
Hi,

I wrote a little shellscript for Opera CSS-based adblocking. With this you don't have to edit configuration files yourself to update it.

**EDIT: Do not use this anymore.. it is out-of-date! Check my post #22 in this thread for a quick guide on using this now!**

---

### Post by blueballs on 2006-05-23
[QUOTE=dakira]Hi,

I wrote a little shellscript for Opera CSS-based adblocking. With this you don't have to edit configuration files yourself to update it.[/QUOTE]


no idea what shellscript is... how do you use this file??

---

### Post by dakira on 2006-05-23
[QUOTE=blueballs]no idea what shellscript is... how do you use this file??[/QUOTE]

A shell script is is little script you can execute in the shell which does some things for you. Like a batch file for Windows.

So if you want to use the script above do this:
1. download the file and close Opera
2. open a terminal
3. cd to the path of the file and unzip it with *gzip -d op_adblocker.sh.gz*
4. change permissions chmod 755 op_adblocker.sh
5. run it with *./op_adblocker.sh*

When its done it will tell you to do some extra configuration inside Opera..

hf
dakira

---

### Post by blueballs on 2006-05-23
[QUOTE=dakira]A shell script is is little script you can execute in the shell which does some things for you. Like a batch file for Windows.

So if you want to use the script above do this:
1. download the file and close Opera
2. open a terminal
3. cd to the path of the file and unzip it with *gzip -d op_adblocker.sh.gz*
4. change permissions chmod 755 op_adblocker.sh
5. run it with *./op_adblocker.sh*

When its done it will tell you to do some extra configuration inside Opera..

hf
dakira[/QUOTE]

:o WOW! thanks for the prompt reply dakira... was expecting a reply like in a few days or so.
i just learnt 3 things here: gzip, permissions and running script!

dakira u rule!!

---

### Post by dakira on 2006-05-24
[QUOTE=blueballs]:o WOW! thanks for the prompt reply dakira... was expecting a reply like in a few days or so.
i just learnt 3 things here: gzip, permissions and running script!

dakira u rule!![/QUOTE]

Hehe ;-) You are very welcome.

Everything for the promotion of the best browser on earth!
dakira *g*

---

### Post by L34NN3 on 2007-01-24
I have a question. Is there anything you can use to adblock the annoying buzzing fly that seems to creep thru the adblock in firefox?

You will save my sanity if you can help...

---

### Post by dakira on 2007-01-25
> **L34NN3 said:**
> I have a question. Is there anything you can use to adblock the annoying buzzing fly that seems to creep thru the adblock in firefox?

Can you give me an example of what you are talking about? Like a site where this occurs? Best would be if you could send me a link to a site with the "fly".

dakira

---

### Post by jake3988 on 2007-01-25
I followed the guide absolutely to the bone.  I double-checked about 3 times.

Not only does it not work but I don't even have the option of 'destory image' in the menu.

Update: Opera does have a 'block content' which for the most part can block just about every ad out there.  If this is new for 9.0 then this entire howto is moot.  So, upgrade and enjoy.  I do like the idea of appending to the already made opera file from a right-click rather than going through the whole 'block content' process.  If anything, to make it a bit faster/simpler.

---

### Post by dakira on 2007-01-26
> **jake3988 said:**
> Update: Opera does have a 'block content' which for the most part can block just about every ad out there.  If this is new for 9.0 then this entire howto is moot.  So, upgrade and enjoy.  I do like the idea of appending to the already made opera file from a right-click rather than going through the whole 'block content' process.  If anything, to make it a bit faster/simpler.

Hi.. before calling this "moot" you should have read the rest of the posts. The original guide was intended for older Opera versions and is obsolete with Opera 9. What is **not** obsolete is the possibility to do CSS-based Ad-blocking which - in my opinion - is far superior to the way Firefox AdBlock and the new Opera9 functionality do it.

You basically use user-css to remove certain elements. The benefit is that the outcome looks pettier. You don't have these huge spaces which remind you of the ads which used to be there. The page just collapses at the point where the ads where.

Just unzip the attached file to *$HOME/.opera/styles/user* and activate the new **AdBlocker-Stylesheet** that appears in the styles menu (Author-Mode dropdown).

You'll never want to miss this again!

dakira

---

### Post by jake3988 on 2007-01-26
It is moot for opera 9.  However, I only mentioned that because of the fact that that is probably the reason why it doesn't work /at all/ for opera 9.

And you're completely wrong.  The 'block content' feature DOES collapse the page (when possible) when destroying ads.

---

### Post by dakira on 2007-01-28
> **jake3988 said:**
> It is moot for opera 9.  However, I only mentioned that because of the fact that that is probably the reason why it doesn't work /at all/ for opera 9.

And you're completely wrong.  The 'block content' feature DOES collapse the page (when possible) when destroying ads.

Err.. You still didn't read the rest of the posts.  I think CSS based adblocking works better than the address-based filter.ini approach (which is used by opera9s block-content feature). This is just a second (and in my opinion) more convenient way of blocking Ads with Opera9 since you include this CSS file ONCE and thats it.. no "right-click->block content" necessaray because the file handles it all. You don't have to block every single ad. And when you revisit a page the ads are still gone and don't appear again just because their URLs changed.

You seem to hate alternatives ;)

---

### Post by juve on 2007-02-27
alternatives are good, but this one is far from perfect.

i'm trying to switch to Opera too, because FF is soooo slow and not stable enough... (or let's better say flashplugin + javascript-lockups usually make it unstable)

But i really miss my straight forward AdBlock + NoScript. It's not only about blocking content but about customizing !! and editing a CSS-file is not the way i'd like to manage my Ad/JS-Killer.
_This is what I (and imho many other users wan't):_
[LIST=1]
[*]a good blacklist (can be very complex using wildcards)
[*]good extensibility (three clicks)
**(1)** right click element -> **(2)** click "block it" -> opens url/filter-editor -> **(3)** Click OK
[*]easy whitelist-capability (two clicks)
**(1)** click on your adblocker-icon -> **(2)** choose whitelist-option for whole site
[*]ability to block images,iframes and backgroundimages, css-classes, tags based on name or id, javascript
[/LIST]

---

### Post by dakira on 2007-02-27
> **juve said:**
> But i really miss my straight forward AdBlock + NoScript. It's not only about blocking content but about customizing !! and editing a CSS-file is not the way i'd like to manage my Ad/JS-Killer.
Noscript is kind of integrated already. You can press F12 and deactivate (or activate) alot of stuff when ever you want. You can also deactivate it by default and just activate it for pages where you want javascript (or other things like java or plugins) to be active.

I know CSS is no adblock replacement (for many). But in my case it does the job better than anything else. I didn't have to edit my adblock file for at least a year and it still works perfectly on all sites I frequent. With adblock the only have to change servers and you have to start blocking again. With my css file the elements from the page are just removed (and stay that way, what ever content they put there). Both methods have their advantages and disadvantages. But I have to say not having to edit the file for a year speaks for itself. On the other hand: IF you need to block something you DO need HTML and CSS knowledge.

The last point of your wishlist would be really nice..

Cheers

---

### Post by phreak0ut on 2008-02-22
> **dakira said:**
> Just unzip the attached file to *$HOME/.opera/styles/user* and activate the new **AdBlocker-Stylesheet** that appears in the styles menu (Author-Mode dropdown).
dakira

I don't see the AdBlocker-Stylesheet :(  [[IMG]http://img20.imageshack.us/img20/3193/screenshotyc7.th.png[/IMG]](http://img20.imageshack.us/my.php?image=screenshotyc7.png)




[[IMG]http://img20.imageshack.us/img20/2662/screenshot1of1.th.png[/IMG]](http://img20.imageshack.us/my.php?image=screenshot1of1.png)

---

### Post by vgrisham on 2008-04-25
This thread was started in 2005 for Opera 8.0. Now that we're at 9.5, Does this method still work?

---

### Post by dakira on 2008-04-26
Yeah.. still works.. get the current version of my css from [here](http://yumdap.net/files/AdBlocker.css) and copy it to *$HOME/.opera/styles/user/*.

Than click on the glasses and enable them in the css menu (author mode). Opera might have changed.. but CSS is still there ;)

---

