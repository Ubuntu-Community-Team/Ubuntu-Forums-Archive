---
title: "Whole folder of movies disappeared"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by fotoflex on 2013-07-15
I tried to move a film into a folder. 
So I clicked 'cut' in the original folder and then I touched the folder named 'films' on my external hard disk,
just to make sure I wasn't trying to put the movie into two folders at the same time.
The folder then disappeared.
A minute or so later, I saw a pop-up; 'Ubuntu has experienced an internal error.'.
And the folder did not come back, either.
I tried Disk-utility to scan the disc and see if the folder had been moved, inside another folder maybe,
but nothing to be seen.
'Search' showed nothing either.
All the movies were Super 8's, which I had digitized over the last few weeks. 
They can't go through the projector again, I was lucky I got as far as I did.
So this means a great loss.
I know the files must be still on the hard disk, and I would be able to retrieve them under Windows,
but how do I go about getting them back running Linux???
Any advice on how to do this would be really appreciated.

---

### Post by theDaveTheRave on 2013-07-16
fotoflex,

sounds like you need a copy of [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), this is in fact what it was originally developed for, but it has become a general file recovery tool.

good luck.

David.

---

### Post by Impavidus on 2013-07-16
+1 to photorec (although I never had to use it myself).

Next time you have to move a file from one drive (or partition) to another, first copy the file (copy-paste or using terminal commands), verify it has been written to the other drive and only then remove it from the first. This is much safer, as you won't lose the file in case your file manager crashes during the operation.

---

### Post by fotoflex on 2013-07-16
Thanks both, I will look into Photorec.
Just to make sure, I didn't lose the file I was trying to move (in fact copy, just as you describe),
I lost the entire folder I wanted to copy*** to***.
No way of avoiding that, except keeping back-ups and back-ups of back-ups.
But they are very large files, to do editing on.
The smaller results I would have backed up, twice even,
but this 'internal error' was a nasty surprise. :(

---

### Post by SeijiSensei on 2013-07-16
> **fotoflex said:**
> but this 'internal error' was a nasty surprise. :(

And a very uncommon one, too.  I'd suspect the disk drive myself.  After you are finished with photorec, run fsck against the partition you were trying to write to.  You might run [smartmontools]("https://help.ubuntu.com/community/Smartmontools") as well.

---

### Post by buzzingrobot on 2013-07-16
That internal error doesn't sound promising, but, just to be sure, does an "ls -a" in the next-directory up, in both folders, show the folder/files are gone?

---

### Post by fotoflex on 2013-07-16
Thanks again.

'[COLOR=#000000]an "ls -a" in the next-directory up', doesn't mean anything to me.
I've tried search, with the names I used for the files.

As for PhotoRec, I've downloaded 6.13 first, and then 6.14, but both give this pop-up when I click exe.
Exe is Windows, and I ran Windows programs with Wine before, but don't get the option here????

P.S.
I thought a screenshot from DiskUtility might be helpful,
but experienced another 'Internal Error', while making one.
After that I tried to copy the Details from the rapport, but can't.
So I made 2 screenshots of that, too.

So, 5 screens;
one from the pop-up,
one from where I downloaded what,
One from DiskUtility,
and two from the InternalError.



[/COLOR]

---

### Post by sandyd on 2013-07-16
sounds like [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1198508](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1198508)

---

### Post by buzzingrobot on 2013-07-16
> **fotoflex said:**
> Thanks again.

'[COLOR=#000000]an "ls -a" in the next-directory up', doesn't mean anything to me.
I've tried search, with the names I used for the files.
[/COLOR]

Open a Terminal window. Navigate to the folder that contained the folder that held the missing files. For example, if the missing files were in   "/media/elements/download/MyFiles", enter "cd /media/elements/download" in the Terminal windows and hit Enter.  Then, do "ls -a" in the Terminal window.  "ls" is the command that lists the contents of a folder. If it shows that the "MyFiles" folder exists, try a "cd MyFiles" followed by an "ls -a" to see if any files are found.

---

### Post by dannyboy79 on 2013-07-16
is your external hard disk still mounted?

---

### Post by fotoflex on 2013-07-16
Thanks,

@ Sandyd,
okay, I've looked at that. But I don't know what to do with it.
I wasn't good at Windows. My laptop crashed, i had a new hdd put in and some extra ram, but wasn't able to re-install Vista.
I had used Ubuntu running from CD, so I installed that instead.

@ buzzingrobot,
I know how to open a terminal window, but not how to navigate to a folder.

@dannyboy79,
Yes, I left everything as it was, haven't shut down either.

---

### Post by theDaveTheRave on 2013-07-17
fotoflex,

photorec is a linux tool that has been ported to windows!

Sorry I didn't realise that the site doesn't have a pure 'linux' download file.

try this

```

sudo apt-get install testdisk

```

That will install a bunch of tools, this will include photorec.

You should be good get those not really deleted files.

this page on [debian]("http://www.debian-administration.org/articles/420") has a brief howto for testdisk, photorec is mentioned as the 5th item down the page.

David

---

### Post by Buntu Bunny on 2013-07-17
It's also in Synaptic.

---

### Post by fotoflex on 2013-07-17
[QUOTE=theDaveTheRave;12734758]fotoflex,

photorec is a linux tool that has been ported to windows!

Sorry I didn't realise that the site doesn't have a pure 'linux' download file.

try this

```

sudo apt-get install testdisk

```

That will install a bunch of tools, this will include photorec.

You should be good get those not really deleted files.

this page on [debian]("http://www.debian-administration.org/articles/420") has a brief howto for testdisk, photorec is mentioned as the 5th item down the page.

David[/QUOTE

Thanks,

I've done that, but the terminal ends like this (see att.).
What do I do next?
When I go to Home and type 'photorec', or 'testdisk', I get a message this can't be found.

---

### Post by fotoflex on 2013-07-17
> **Buntu Bunny said:**
> It's also in Synaptic.

I Googled that, and it says that in ubuntu 11.10 Synaptic changed to Ubuntu Software Center.
'Photorec' isn't found, but 'TestDisk' is.
It is already installed.
That is right, i've just done that, see post above.
But I don't know how to open it. :(

---

### Post by Buntu Bunny on 2013-07-17
> **fotoflex said:**
> I Googled that, and it says that in ubuntu 11.10 Synaptic changed to Ubuntu Software Center.

Synaptic Package Manager is not longer part of the default Ubuntu package. I can be installed via Ubuntu Software Center. It includes a lot of things Software Center doesn't, so it's handy to have around. 

> **fotoflex said:**
> 'Photorec' isn't found, but 'TestDisk' is.

Correct, but Photorec is mentioned in the description.

> **fotoflex said:**
> It is already installed.
But I don't know how to open it. :(

Apparently there is no GUI. If you type 'testdisk' at the prompt in terminal it comes up in terminal. I've never used it so will leave the how-to details to the more experienced. There may be a tutorial online. I'll see what I can find. 

Fotoflex, I'm glad you posted this question because this thread has been helpful to me too.

---

### Post by slickymaster on 2013-07-17
> **Buntu Bunny said:**
> ... Apparently there is no GUI. If you type 'testdisk' at the prompt in terminal it comes up in terminal. I've never used it so will leave the how-to details to the more experienced. There may be a tutorial online. I'll see what I can find...

[PhotoRec Step By Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

---

### Post by Buntu Bunny on 2013-07-17
Here are a few tuts I've bookmarked for myself

[Recovering Lost data with photorec]("http://www.opensourcebistro.com/Tutorial/VL60/Trouble-Shooting/Photorec/photorec.htm") (video)
[Photorec Step By Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") (wiki article, looks a bit techy)

---

### Post by Buntu Bunny on 2013-07-17
> **slickymaster said:**
> [PhotoRec Step By Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

Thanks slickymaster! I found that one too. I think it will make sense when going through it step by step.

---

### Post by theDaveTheRave on 2013-07-17
Sorry but I'm not going to be much more helpfull as I've never had to use photorec or testdisk in a serious manner


However, if you really get stuck on the step by step guide posted by slickmaster remember to post the problems here, I have a tutorial from a magazine on photorec, so it may have some extra details over the guide.

David

---

### Post by fotoflex on 2013-07-17
@ Slickymaster,

thanks. Handy!

@ ubuntu bunny,

> [COLOR=#000000] If you type 'testdisk' at the prompt in terminal it comes up in terminal.[/COLOR]

Well, it should. But it doesn't. I see this:

> Sorry, there nothing that matches your search.

---

### Post by fotoflex on 2013-07-17
> **theDaveTheRave said:**
> Sorry but I'm not going to be much more helpfull as I've never had to use photorec or testdisk in a serious manner
However, if you really get stuck on the step by step guide posted by slickmaster remember to post the problems here, I have a tutorial from a magazine on photorec, so it may have some extra details over the guide.
David

Thanks, but you're way ahead of me!
I downloaded Synaptic, nice, has an Android feel to it.
I used that to uninstall TestDisk, that I can't get to open,
and installed Teskdisk again.
But with the same result as mentioned in the post above.
That is the next logical step: to open Testdisk!

Spock? Where is your Vulcan brain when I need it?

---

### Post by slickymaster on 2013-07-17
> **fotoflex said:**
> Thanks, but you're way ahead of me!
I downloaded Synaptic, nice, has an Android feel to it.
I used that to uninstall TestDisk, that I can't get to open,
and installed Teskdisk again.
But with the same result as mentioned in the post above.
That is the next logical step: to open Testdisk!

Spock? Where is your Vulcan brain when I need it?
Well, if it's properly installed, when you run ```
~$ testdisk
``` you should get this (See the attachment below)
What happens when you run```
photorec
```

---

### Post by slickymaster on 2013-07-17
Another thing, can you please post the output of:```
dpkg --get-selections | grep testdisk
```in order to confirm if you really have it installed, or not.

---

### Post by fotoflex on 2013-07-17
> **slickymaster said:**
> Another thing, can you please post the output of:```
dpkg --get-selections | grep testdisk
```in order to confirm if you really have it installed, or not.

And both opened! 
So it must be installed.
Thanks very much, all.
Now to try and get some files back!

---

### Post by slickymaster on 2013-07-17
You're welcome. Just glad you've got it running.
Please don't forget to mark this thread as SOLVED. Follow the link in my signature if you don't know hot to do it.

---

### Post by fotoflex on 2013-07-17
> **slickymaster said:**
> You're welcome. Just glad you've got it running.
Please don't forget to mark this thread as SOLVED. Follow the link in my signature if you don't know hot to do it.

Well, I've yet to see if PhotoRec finds anything (a lot of step by step reading to do still).
And if it does, I'll know only whether the films are just inexplicably moved or the entire folder deleted.
That's not solved yet! :(

---

### Post by slickymaster on 2013-07-17
> **fotoflex said:**
> Well, I've yet to see if PhotoRec finds anything (a lot of step by step reading to do still).
And if it does, I'll know only whether the films are just inexplicably moved or the entire folder deleted.
That's not solved yet! :(

No worries. We'll be here in case of need.

---

