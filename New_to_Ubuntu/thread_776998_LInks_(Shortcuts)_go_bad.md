---
title: "LInks (Shortcuts) go bad"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-05-01
On my desktop on Ubuntu, I created about 20 links (or shortcuts) that point to various documents in my computer. The shortcuts normally work fine , as they are supposed to. However, lately, I have been having trouble with my shortcuts going bad. If I click on a bad shortcut I get a message "The link to XXX is broken. Move it to trash?"

This problem has happened at least two or three times, usually, right after I reboot my computer. For some reason, the rebooting process, or something else, is causing the links to be broken.

Can anyone tell me how I can make all my links on my desktop permanent?

Thanks.

JBA2337

---

### Post by talsemgeest on 2008-05-01
Is the location still there? As in is the file the shortcut points to still where the shortcut says it is?

---

### Post by Paqman on 2008-05-01
Can you supply an example of what path one of the dodgy links is trying to use?

---

### Post by JBA2337 on 2008-05-01
Only the links go bad. The files that the link points to are still there. Example: Link on my desktop points to the folder Videos. The folder called Videos is still OK, but if I click on the link, I get a message that the link is broken. It doesn't work. The only solution is to delete the bad links, and make new ones. But the new ones eventually have the same problem. Is there a` way to prevent the link from being broken??

JBA2337

---

### Post by talsemgeest on 2008-05-01
That sounds like a pretty deep down problem, sounds like its in the kernel itself.

---

### Post by aeiah on 2008-05-01
> **talsemgeest said:**
> That sounds like a pretty deep down problem, sounds like its in the kernel itself.

it wont be in the kernel, it'll be in nautilus or gnome perhaps.

how are you creating the links?

---

### Post by Paqman on 2008-05-01
> **JBA2337 said:**
> Example: Link on my desktop points to the folder Videos. The folder called Videos is still OK, but if I click on the link, I get a message that the link is broken.

Can you post the full path to the folder? Eg: is it something like /media/Videos or /home/username/Videos? Is it on an internal or an external drive? Do you know if it's on your root partition?

---

### Post by JBA2337 on 2008-05-01
I create links as in the following example. The folder that I want to create a link for is /home/jim/Videos. To create the link, I go to /home/jim/videos, and I click on the word Videos with both mouse buttons depressed. Then, still with both buttons depressed, I drag the word Videos to my desktop. Then when I release the mouse buttons, a dialog box pops up. I then click on the option that says "Link Here". This procedure makes a link on my Desktop for Videos.

By the way, I just did this again, rebooted my computer, and when it came up, the link that I had just created was broken.
JBA237

---

### Post by JBA2337 on 2008-05-05
I just noticed that the only links that go bad are the one that link to a location that is not on the same partition as Ubuntu.

For example, a link to a text file, where the original text file is located somewhere in the Filesystem of Ubuntu (on the Linux ext3 partition)works.

However, a link to a text file, where the original file is located on my Windows partition (NTFS) does not work. The link to a file on the NTFS partition will work, as long as I am using Ubuntu. But If I reboot my system, and start up Ubuntu again, the links to all the files on the NTFS partition do not work.

Does anyone have any idea how to solve this problem?

JBA2337

---

### Post by Valloric on 2008-05-18
I am having the EXACT same problem. Links that point to folders on other drives (the drives I had from Vista) are broken after a reboot. 

BUT!

The links can get "unbroken". For instance, Ubuntu boots up, and there are no "drive" icons on the desktop. Then I start the file browser, and click on links to my drives on the left, in the panel "Places". Suddenly, the drives are on the desktop again, and the desktop links to folders on those drives get "unbroken". The icons for the links are still those "gears", but if I double-click them, they open without problems, and the images turn back into folder icons.

Seems like a bug to me.

EDIT:

Silly me, the NTFS drives were not being auto-mounted, and that made the links go bad. For the solution, look [here]("http://ubuntuforums.org/showpost.php?p=4861607&postcount=3").

---

