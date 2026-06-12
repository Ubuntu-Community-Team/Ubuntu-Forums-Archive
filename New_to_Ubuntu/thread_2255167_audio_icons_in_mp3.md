---
title: "audio icons in mp3"
date: 2014-12-02
forum: New to Ubuntu
---

### Post by shadoogie2960 on 2014-12-02
Recently I have digitized some music-numbers to .mp3-files and generated tags with 'easyTAG'.
Some files show up in Nautilus with a standard audio icon and others show up with the front-cover of the music-CD (see attachment).
I added the cover-image-file to every mp3-file. In easyTAG I see no difference between the files icons. In Nautilus they are not all the same ???
Can someone please explain me what I am doing wrong ?
I did try to modify the tags with 'mp3tag' under Windows (in VirtualBox) and I get the same result !?

[ATTACH=CONFIG]258340[/ATTACH]

---

### Post by coldcritter64 on 2014-12-02
Try deleting the folder "/home/<your-username>/.thumbnails/**fail**" then refresh the file browser folder view where those blank icons are showing. The current batch without the icons should generate new icons. It sometimes takes a couple of goes to get them all fixed if there are a few like in your attachment. gnome-thumbnailer seems to randomly fail when creating a lot of icon thumbnails.

Gnome-thumbnailer has caused this problem for me so often that I store a script in "/home/<user>/bin" called "nuke-thumbs" just to clear the failed thumbnails as necessary ... 

> ```
#!/bin/bash
#
# Remove failed thumbnails for refreshing folder icons.
#
#

rm -r ~/.thumbnails/fail && notify-send "Failed thumbnails removed !";

exit 0
``` If you use this with no "fail" folder present in the ~/.thumbnails folder the script fails showing the folder wasn't there anyhow ... so nothing happens. If the folder is present the notify-send message lets you know the folder was removed.

Then in terminal I can just type nuke-thumbs and press enter **OR** point a panel launcher at the script (note I'm on xfce not the standard Ubuntu, can be done manually in Ubuntu with a ".desktop" file in "~/.local/share/applications". Such a launcher can then be dragged onto the Unity bar etc.) to activate the failed thumbnail removals. **Note:** the "**~**" symbol just used in the paths above are a system variable for you home folder, "/home/<your-user-name>/"

Once cleared, refreshing the view in your file browser window will re-create the blank icons.

I never did find out the problem with gnome-thumbnailer, I just got used to using this workaround. Cheers, coldcritter64

---

### Post by shadoogie2960 on 2014-12-03
Thanks, coldcritter64, for your clear reply.
I tried what you suggested but there is no 'fail-directory' ...
I only see one subdirectory in .thumbnails, named 'normal'
And this one contains ten files, all .png, consisting of 32 hex-numbers ... ???

My laptop runs on Ubuntu 14.04 LTS and is a Medion AKOYA P7818

Shadoogie2960

---

### Post by lisati on 2014-12-03
On a side note, nice choice of tracks (and user name)..... :D

---

### Post by coldcritter64 on 2014-12-03
> **shadoogie2960 said:**
> ...
I only see one subdirectory in .thumbnails, named 'normal'
...
That surprised me. You seem to have a bit deeper problem with the gnome thumbnailer ... wait for further replies from other helpers.

> **shadoogie2960 said:**
> ...And this one contains ten files, all .png, consisting of 32 hex-numbers ... ???Yes, the "hex-numbered" files sound perfectly normal. 
I've never seen a missing "fail" directory before which stumps me a bit ... :confused:, I will research a bit more on this and get back soon, there may be a bug listed somewhere that may reveal what is going on in this situation.

Just a side note: I have used easytag before to add the images to mp3  files like you did here. It is a slow and involved process which is easy to miss a file (or a few) in the process. 
Suggestion: Try loading those files again in easytag and check you have not missed setting the images in them as "Type: Cover (front)" see attached screenshot. 
If I recall correctly (it is a VERY long time since I tagged all my music collection) I missed this setting on a few files and the thumbnailer missed them. My usual method of refreshing thumbs failed then as well until I added the "Type: Cover (front)" category. A possibility for you to check.

---

