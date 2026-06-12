---
title: "[SOLVED] Copy DVD"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-10
I've tried using K9Copy to create an ISO file with Intrepid. The ISO just disappeared. I understand K3b is great to burn with... But I can't seem to get that far. K9Copy used to work with 7.10. Then it quit for some reason. It looked like a good time to move on to a later version of Ubuntu. What's good to use with Intrepid, or do I need to do something to get K9Copy to work ?

---

### Post by fooman on 2008-11-10
i've used k9 copy many times and never had a problem...then again,  i have never saved any dvd as a iso.  i have just used k9 copy to copy and burn the disc.

any reason why you need to save as an iso?

---

### Post by CoCoKnots on 2008-11-10
Hi Fooman,
I assumed they needed to be in an ISO format in Ubuntu to be able to burn successfully onto a DVD. What are the options ???

---

### Post by CoCoKnots on 2008-11-10
Hi Fooman,
I assumed they needed to be an ISO format in Ubuntu to burn successfully onto a DVD. What are the options ???

---

### Post by fooman on 2008-11-10
in k9 copy,  change the "output device" to your dvd burner (same as input device unless you have 2 drives).  change it by clicking the down arrow at the end of the box that says "ISO image".

after that,  click "open" and it will read your disc.  when it completes,  just click "copy" and it will copy the disc to your /tmp folder.  when it completes that,  it should open the drive and ask you to place a blank disc in the drawer.

do that and click burn.

now realize its been awhile since i've copied a disc....but i believe thats the way i have done it.

btw,  you can change the output directory from /tmp by clicking on configure k9copy > dvd
you can also configure to burn with k3b in that same configuration box...but i think k9copy will do the job just fine on its own.

---

### Post by CoCoKnots on 2008-11-10
I'll give that a try & reply... Thanks

---

### Post by fooman on 2008-11-10
i have a feeling the iso's that have "disappeared"...are in:

/tmp/kde-<your user name>/k9copy/

---

### Post by CoCoKnots on 2008-11-10
'...and it will copy the disc to your /tmp folder. when it completes that, it should open the drive and ask you to place a blank disc in the drawer.'

It looks like it's copying to somewhere. It doesn't open or ask for a blank disc... & I don't see a 'Burn' button. I'm trying the procedure again.

---

### Post by CoCoKnots on 2008-11-10
'i have a feeling the iso's that have "disappeared"...are in:

/tmp/kde-<your user name>/k9copy/'

That's where they are... How do I get them out ?

---

### Post by fooman on 2008-11-10
i am trying to copy a disc now to see how its done...i should not have tried from memory.

i'll see how it goes.

one thing i forgot to say...after you "open" the disc in k9copy,  you need to look in the "title" box and check off the title's you wish to burn onto the copy.  you can try the entire disc,  or you can pick and choose which ones,  maybe cut out some menus and such.  then you click "copy".

if you skip that step...you will not get a copy of the dvd.  probably just a few menus if anything.

when that completes,  the drawer should open *or* a message box may pop up telling you to replace disc with a blank dvd.

i'll let you know in a few minutes when i get that far.

---

### Post by CoCoKnots on 2008-11-10
I remember the part about checking off the titles before you try to copy... However, the disc door is not opening. I thought it should also. Are you working with Intrepid also. I have a feeling something strange is going on with this as well.

---

### Post by fooman on 2008-11-10
your right,  the drawer does not open on its own.  a message box does pop up though and it instructs you to place a blank disc in the drive.

after you do that,  click "continue" (not burn....sorry) in that same message box and the burn process will start.

mine is burning as i write this.

---

### Post by CoCoKnots on 2008-11-10
OK... That makes since. Except I am not getting the window with instructions like you are talking about. I waited for quite a while for something to happen. I even tried reloading K9Copy from Sys>Admin>Syn/Pkg/Mgr... It didn't make any difference. What ver of Ubuntu are you using ?

---

### Post by fooman on 2008-11-10
i am using intrepid.  the box pops up as soon as the copy process is complete.  there is no wait at all.

---

### Post by CoCoKnots on 2008-11-10
Great... At least we know we are using the same version of Ubuntu. Any ideas about what I can do to get this to work ?  It almost sounds like K9Copy in corrupt in the download Sys>Admin>Syn/Pkg/Mgr before it's installed ??? I did an update earlier today. It included some K9copy files.

Maybe I need to put this off until I receive another update ?:confused:

---

### Post by fooman on 2008-11-10
it comes up in a separate window from k9copy...are you sure it does not come up somewhere on your screen? ...maybe obscured by another open window, or even k9copy itself?

i am going to get to that point again and i'll take a screenshot to show you.

---

### Post by CoCoKnots on 2008-11-10
Great... Thanks. It might help to have an idea of what to look for.

---

### Post by fooman on 2008-11-10
box is in upper left:

[http://ubuntuforums.org/attachment.php?attachmentid=92144&stc=1&d=1226374840](http://ubuntuforums.org/attachment.php?attachmentid=92144&stc=1&d=1226374840)

---

### Post by CoCoKnots on 2008-11-10
Thanks Fooman,
I do not have a window like this. I'm not really sure what to do except reload another update when it comes. I think I need to call it a night for this evening. 'Start again in the morning. Thanks again for all the help.

---

### Post by fooman on 2008-11-11
checking the k9copy website,  i see they have a list of prerequisites.  i checked my system and found that i already have them all installed.  check in synaptic and make sure you have all of the following packages installed,  if you are missing any...then install them and try k9 again.  open synaptic and search for/install:

    * DVDAuthor
    * libdvdread
    * growisofs (part of the "dvd+rw-tools" in synaptic)
    * mencoder
    * mplayer
    * libhal
    * libdbus
    * libdbus-qt
 
[http://k9copy.sourceforge.net/index.php](http://k9copy.sourceforge.net/index.php)

---

### Post by CoCoKnots on 2008-11-11
Thanks Fooman,
I'll check that next. Sorry for the delay in getting back to you. My system died & couldn't get back on the forum... I eventually gave up & went to bed.

---

### Post by CoCoKnots on 2008-11-11
OK... I checked into the Sys>Admin>SynPkgMrg. This is what I have. I have to admit, I don't know what the difference is... Or if there is any.

Required:    Current Sys>Admin>SynPkgMgr:

* DVDAuthor    > DVDAuthor
* libdvdread   > libdvdread3
* growisofs    > (part of the "dvd+rw-tools" in synaptic)
* mencoder     > mencoder
* mplayer      > mplayer
* libhal       > libhal1
* libdbus      > libdbus-ruby, libdbus-ruby1.8
* libdbus-qt   > libdbus-1-qt3

Will these work to get k9copy to function correctly ???

---

### Post by johntravis on 2008-11-11
Bring up k9copy--install dvd to be copied---click open--set input/output devices the same--left tree click first box and all will be selected--click copy--when copy is finished pop-up window will state to put a blank dvd disk in burner (draw may open automatically or you may have to open manually)--do so then click continue--you may get a pop-up window stating error and to put another blank dvd disk in, I was using a dvd-r and got that message, using a dvd+r the burning process continued with no other problems.

---

### Post by CoCoKnots on 2008-11-11
Hi John,
This has been an issue between Intrepid & myself.
I'm doing exactly what you are describing... the only problem is,,, the door doesn't pop open,(which we can work around), I'm not getting the second window requesting the blank DVD & as a result, there isn't a 'Burn DVD prompt. There has to be something missing in this formula somewhere. Is there perhaps something that needs to triggered in the terminal?

---

### Post by johntravis on 2008-11-11
There have been numerous problem with 8.10 (I tried it for awhile) that I went back to 8.0.4.1 LTS, less problems to overcome. I have not been a Ubuntu user for long but once I got this computer to my liking I am staying with 8.0.4.  These forums are great for learnig/doing,do not give up, but if you still cannot get 8.10 to do your bidding go back to 8.0.4.1LTS

---

### Post by johntravis on 2008-11-11
Everything fooman is saying is good so it must be a bug in Interpid, try 8.0.4.1 LTS

---

### Post by CoCoKnots on 2008-11-11
Thanks John,
I think I'm right behind you. I can't get 'ThinkOrSwim'(my trading program) to work either. That's one program I have to get working. Some kind of conflict 'Java.lang.NullPointerException' error when I start up. I just don't have time to play with this... Thanks again.

---

### Post by sdowney717 on 2008-11-11
I use DVDShrink or DVDFab5 in wine and with IBEX it works perfectly.

K9 copy in IBEX always crashed on me.

---

### Post by fooman on 2008-11-12
> **CoCoKnots said:**
> 'i have a feeling the iso's that have "disappeared"...are in:

/tmp/kde-<your user name>/k9copy/'

That's where they are... How do I get them out ?

since you know where they are...have you tried burning those iso's with k3b, etc

in k3b,  when it opens choose burn dvd iso image

where it says "image to burn"...click the button at the end of the box and navigate to the file in your tmp folder.

maybe that will work for you (hope so).

---

### Post by peterx2 on 2008-11-15
k9copy comments.. I have successfully copied DVD's but now that they have changed the system to 8.10 it is more difficult. Basically the problem is that the burners are not linked properly. You cant automatically link to K3b or any automatic burner anymore. You can write an .iso to a file however and then pick that .iso to burn.. In the setup for DVD turn off any burners that have been checked. Put the default location for the intermediate files up in your home area since you have to manually erase these from time to time. They are small files and apparently contain setup info for the specific project.

When you select the iso output you will also select a target destination.. I selected the desktop. Fiddling with this in this way you dont have to write DVD's until you know that there is something to write and it costs you nothing but time to get it right.

By the way I tried this in both Ubuntu and Kubuntu. Ubuntu seems a little clearer to me and works ok.. Kubuntu probably works now that I have eliminated the burner problem but I havent tried to test that again. I have tried the new K9copy 2.10 version as well and there is no change in the problem but some new screens that are helpful. You have to download this from a site that carries k9copy separately.

---

### Post by jalirious on 2008-11-21
Nowt to do with ibex, but on hardy I find the fastest & most stable way is 

decrypt using dvd decrypter on wine, -> 7-8 gig .iso
shrink using k9 copy -> /tmp/kde-username/k9copy/dvd 
convert to iso using k3b (I just create the image, don't burn right now)

Dvd Shrink on wine works as well, but is slower and more prone to crashing.

//Edit

The above still works, but just using k9copy and k3b is far faster and takes up less space.

---

