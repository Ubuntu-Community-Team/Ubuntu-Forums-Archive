---
title: "ttf font troubles - RESOLVED"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by already_used on 2008-09-06
I have resolved this problem but am posting anyway in case it helps someone else.

Also, did I miss a step or do something wrong?:confused:

I'm extremely new to Ubuntu.
I previously ran OpenSUSE 10.x with Gnome and was able to install TTF fonts, but could not get them to render correctly in Ubuntu; I just get the lovely boxes.
I am running desktop 8.0.4

Here are the steps that I have done:
[LIST]
[*]cd /usr/share/fonts/truetype
[*]sudo mkdir ./ttf-mine
# making a directory for my fonts to go into, using /usr/share so all users have them
[*]gksudo nautilus ./ttf-mine
[*]copied fonts from flash drive to ./ttf-mine
[*]fc-cache -f -v
[*]output was: 
...
/usr/share/fonts/truetype/ttf-mine: caching, new cache contents: 16 
fonts, 0 dirs
...
fc-cache: succeeded
[*]reboot
[/LIST]

I don't remember if they were visible before or after the reboot, but in both Inkscape and gedit the fonts are listed (textually) however any of the fonts that I have added are displayed as those annoying blocks.

I *finally* figured out after browsing to that folder what the problem was. Looking at the permissions of other fonts, I found that they were:
owner: root: read-write
groups: root: read-only
other: users: read-only

But, the files in the folder I had just created were:
owner: root: read-write
groups: root: -
other: users: NONE

So to fix that,
gksudo nautilus /usr/local/fonts/truetype/ttf-mine

then selected all files (ctrl + a) and went to properties
changed the group's permissions to readonly
changed the users to readonly

And now my fonts work!

I don't remember seeing a step that set the permissions on the new files or that folder, and I followed the steps I found in other posts. I also retraced all of my steps (after listing them above) with a new folder and a few other fonts to double check myself, but it did the same thing; groups had - and users had NONE.

So, is this a bug, or was I missing a step? 

And Mods if this has been posted elsewhere feel free to delete this, but of all the articles I read, none of them mentioned this error.

---

