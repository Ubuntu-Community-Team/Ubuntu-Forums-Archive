---
title: "Why FireFox 2 does not integrate with Hardy Heron?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by legolas_w on 2008-05-08
Hi
thank you for reading my post
I removed Firefox 3 from Hardy heron and I installed FireFox 2.0 in order to have all my old settings and extensions.

Now it does not completely integrate with gnome, for example I can not click on a link in thunderbird in order to open it in the browser and I should copy and paste the link, it is the same for pidgin,.....


Is there any way to make it fully integrate with hardy heron as it was with Gutsy Gibbon?

I attached an screenshot of "Preferred Applications" to show what I have done.
I am wondering why Firefox is not in the list of selectable applications and Opera is?

Thanks



[IMG]http://tinypic.info/files/pq0xogx173gebciszvmx.png[/IMG]

---

### Post by angry_johnnie on 2008-05-08
In the box where it says **command**, change **firefox** to **firefox-2**.

---

### Post by deetox on 2008-05-09
i have changed firefox to firefox-2 on that Command line. originally it had firefox %u and i just changed it to %s just now.

i still only get a new window (doesnt put the new link into a tab...) and it just goes my homepage (doesnt go to the link...). ive tried restarting pidgin and ff to try to make it work. do i need a restart?

im not rm'ing any directories either. got my tabs, bookmarks, and passwords saved that i wish to keep...

halp?

---

### Post by philinux on 2008-05-09
Hardy is a Long Term Support version, LTS, and as such FF3 is the new version. The fact it's still beta well... thats another story.

---

### Post by deetox on 2008-05-09
philinux: epic fail...no help at all. work the problem, dont post useless drivel.


also, nm... got it to work just now.

had to install firefox-2-gnome-support and now it shows up in Preferred Applications (without an icon tho...), and i get a radio button for "Open link with web browser default" (firefox %s) which my default is to open up in a new tab, along with "Open link in new window" (firefox -new-window "%s") and "Open link in new tab" (firefox -new-tab "%s").

---

### Post by philinux on 2008-05-09
Firefox two will no longer be supported by mozilla very shortly. No security updates.

---

### Post by llamakc on 2008-05-09
> **deetox said:**
> philinux: epic fail...no help at all. work the problem, dont post useless drivel.


also, nm... got it to work just now.

had to install firefox-gnome-support and now it shows up in Preferred Applications (without an icon tho...), and i get a radio button for "Open link with web browser default" (firefox %s) which my default is to open up in a new tab. "Open link in new window" (firefox -new-window "%s") and "Open link in new tab" (firefox -new-tab "%s").

Don't be rude or go elsewhere please.

---

### Post by TheLions on 2008-05-09
> **deetox said:**
> philinux: epic fail...no help at all. work the problem, dont post useless drivel.
.

He only answered the Question!

---

### Post by deetox on 2008-05-09
> **philinux said:**
> Firefox two will no longer be supported by mozilla very shortly. No security updates.

not a problem, ill keep using the 2.0.0.x branch until ff3 is out of beta and  working correctly. hopefully the bugs will be worked out by 8.10...


PS: Are you a bot?


llamakc, TheLions: read what i wrote and focus on the problem i had. philinux telling me about ff2 support expiring "very shortly" is not even in the same ballpark as my question...

---

### Post by philinux on 2008-05-09
There is an addon, cant remember it's name that lets you install old addons without a FF3 validation check. 
FF3 full release is out soon so all addon developers should be updating there code very soon.
I was answering the OP.

---

### Post by deetox on 2008-05-09
> **philinux said:**
> There is an addon, cant remember it's name that lets you install old addons with a FF3 validation check. 
FF3 full release is out soon so all addon developers should be updating there code very soon.
I was answering the OP.

THANK YOU FOR QUOTING!!! wish you would have expressed that earlier...

[QUOTE=TheLions]He only answered the Question![/QUOTE]

im not the originator of the thread, i just had a similar problem.

---

### Post by philinux on 2008-05-09
I'm not a computer. Memory only works intermittently.

---

### Post by the-edmeister on 2008-05-09
> **philinux said:**
> Firefox two will no longer be supported by mozilla very shortly. No security updates.
Firefox 2.0 will continue to be supported with security updates for 1 year after Firefox 3.0 is officially released, just like Mozilla did with 1.0 and 1.5 .

---

### Post by Mander on 2008-06-19
Try MR Tech Local Install:

[https://addons.mozilla.org/en-US/firefox/addon/421](https://addons.mozilla.org/en-US/firefox/addon/421)

I think it's now working with Firefox 3, but I haven't tried it yet.  I use it under Firefox 2.

You can always try changing the Max Version number in install.rdf for specific extensions.  So far it's worked with most things I've tried, although there's always the possibility that it will break Firefox or else just not work.

See here for some instructions:

[http://easygeek.org/index.php?option=com_content&task=view&id=19&Itemid=26](http://easygeek.org/index.php?option=com_content&task=view&id=19&Itemid=26)

---

