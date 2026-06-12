---
title: "Word 2016 and onedrive - how to install?"
date: 2018-04-02
forum: New to Ubuntu
---

### Post by sinqbad on 2018-04-02
I'm moving to ubuntu since I can't use windows anymore. Doing a PhD and I need word 2016 (not just 2013) is there a way to get word 2016 and a working onedrive folder that syncs. This is the only thing that I need that can't be replicated in linux.

---

### Post by jpberes on 2018-04-02
Hi there,
Word 2016 is Microsoft and as such Microsoft can not run natively on Linux, however there are some ways around.
* You can use LibreOffice a Microsoft alike office suite ... LibreOffice Writer, can open and write Microsoft office formats such as .doc or .docx
* You can try to use WINE or PLAYONLINUX tool to run Microsoft applications (installation of Ms-Word in Wine)
* You can install MS Windows in a Virtual Machine (VirtualBox) and install MS-Office in there
OR you can use Ms-Office Online through your Hotmail or Live account .. upload and download documents from the cloud ;-)
Kind regards,
JP

---

### Post by sinqbad on 2018-04-02
* You can try to use WINE or PLAYONLINUX tool to run Microsoft applications (installation of Ms-Word in Wine)
This was what I was thinking. How would I go about doing this?

---

### Post by SeijiSensei on 2018-04-02
[https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

---

### Post by sinqbad on 2018-04-02
> **SeijiSensei said:**
> [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu)

Thanks, I was aware of that and it doesn't explain how to install word 2016 or office. Maybe because I'm not a specialist I don't know what language is being used.

---

### Post by kerry_s on 2018-04-02
you can use the web versions, like:
[https://office.live.com/start/Word.aspx](https://office.live.com/start/Word.aspx)

---

### Post by sinqbad on 2018-04-02
I need zotero support and features in word 2016. Libreoffice and the web versions don't cut it. And I'm kinda sick of people suggesting alternatives (that are clearly lackluster) rather than just helping me how to install word (in this case using WINE)

Also, how do I get my onedrive to sync to ubuntu. My calibre library is on it.

---

### Post by kerry_s on 2018-04-02
> **sinqbad said:**
> I need zotero support and features in word 2016. Libreoffice and the web versions don't cut it. And I'm kinda sick of people suggesting alternatives (that are clearly lackluster) rather than just helping me how to install word (in this case using WINE)

no need for attitude. 
stock wine is not going to run past office 2013.
[https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install](https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install)

---

### Post by HermanAB on 2018-04-02
You can use Codeweavers Crossover.  It cost a few bob, but they provide support and it sounds like you need support:
[https://www.codeweavers.com/compatibility/crossover/microsoft-office-2016](https://www.codeweavers.com/compatibility/crossover/microsoft-office-2016)

Crossover is the paid for version of WINE and it is rather better than the free version.  Codeweavers are the people that maintains and develops WINE, so your subscription will help the project.

---

### Post by Mark Phelps on 2018-04-02
OK, then you can't "move to Ubuntu" -- because you have a critical Windows dependency that will not work in Linux.

You could always install VirtualBox and, in there, install a version of Windows.

---

### Post by kerry_s on 2018-04-02
> **Mark Phelps said:**
> OK, then you can't "move to Ubuntu" -- because you have a critical Windows dependency that will not work in Linux.

You could always install VirtualBox and, in there, install a version of Windows.

there's also the duel boot option. ;)

---

### Post by sinqbad on 2018-04-02
> **kerry_s said:**
> no need for attitude. 
stock wine is not going to run past office 2013.
[https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install](https://www.codeweavers.com/support/wiki/linux/linuxtutorial/install)

sorry didn't mean for that to come across as having attitute. I'm more defeated. I can't afford a new laptop right now and I need word 2016 for my research. Which is a shame because everything else about ubuntu is great and I'm happy with it. I might get a little pissy because everyone else suggests google docs, word online, libre, open office sometimes, latex etc and I've heard it a million times. I know people are trying to help and that libre is a fine replacement for 90% of users but I know what features I need and I know that I need 2016 and I hate having to justify myself everytime for using non-free software (honestly, while libre is a fantastic product comparing the output a dev of professional volunteers vs paid coders whose only job is to make word is a bit naive). 

I'll look into codeweavers thank you.

---

### Post by QIII on 2018-04-03
The Linux alternatives are not drop-in replacements.  Period.

If you need Microsoft tools, you need them.

Your PhD studies far outweigh any other consideration and I would encourage you to use whatever tools/OS you need to use to reach that goal.  There is simply nothing more important.  I am not a Linux apologist.  I'm a pragmatist.  Use what works.

I would also suggest that switching the arrangement might be better:  Have Windows as your primary installed OS and run Linux in a VM.  That way if you botch your Linux installation you don't risk your PhD work.

The last paragraph of all my articles on my (pretty much languishing) blog is:

> Legal Disclaimer:  I am not an Ubuntu apologist, but I do use Ubuntu and Kubuntu.  I am not a Fedora apologist, but I do use Fedora.  I am not a Windows apologist, but I do use Windows.  I'm not a FOSS apologist, but I use FOSS tools when I can and when they fit the job at hand.  I don't find any sense in a religious affiliation with tools and operating systems.  That's just asinine.

---

### Post by sinqbad on 2018-04-03
I would go back to windows just for the ease, but my laptop broke down and I'm using a crappy 7 year old laptop (which ubuntu works perfectly on) and can't afford a new one atm (or get money for a new one). So trying to figure another way to do this.

---

### Post by QIII on 2018-04-03
What are the specs?  Let's see if you can run Windows in a VM.  A VM avoids the issue with unpredictable results using Wine/CodeWeavers.

---

### Post by sinqbad on 2018-04-03
> **QIII said:**
> What are the specs?  Let's see if you can run Windows in a VM.  A VM avoids the issue with unpredictable results using Wine/CodeWeavers.

How can I do this? CPU-G doesn't seem to be working.

---

### Post by QIII on 2018-04-03
There is a special, mystical, magical, virtual directory that exists in memory that contains a bunch of zero-length files that you can, nonetheless, examine.  It's called /proc.

There are a lot of interesting things in there, but what we are interested in is /proc/cpuinfo.

We can get the model of your cpu thus:

```
cat /proc/info | grep model
```

which will pipe the contents of the file to grep and return all the lines were there is a match on the regex 'model'.

That will give us enough to go on.

---

### Post by QIII on 2018-04-03
Just by way of a bit of research:

WineHQ has OneDrive rated as "Garbage" and Word 2016 not rated at all.

[Codeweavers rating for Microsoft Office 2016]("https://www.codeweavers.com/compatibility/crossover/microsoft-office-2016") shows OneDrive as 2/5 (probably hardly usable) and Word 2016 as 4/5 (probably usable with some issues).

So, the main thing here is that we need to get you up and running with Word 2016 and OneDrive in the best fashion possible.

---

### Post by sinqbad on 2018-04-04
> **QIII said:**
> Just by way of a bit of research:

WineHQ has OneDrive rated as "Garbage" and Word 2016 not rated at all.

[Codeweavers rating for Microsoft Office 2016]("https://www.codeweavers.com/compatibility/crossover/microsoft-office-2016") shows OneDrive as 2/5 (probably hardly usable) and Word 2016 as 4/5 (probably usable with some issues).

So, the main thing here is that we need to get you up and running with Word 2016 and OneDrive in the best fashion possible.

paddy@paddy-U36SG:~$ cat /proc/info | grep model
cat: /proc/info: No such file or directory
 
But I just looked up my Laptop and it's Intel®  Core™ i5  2540M/2430M/2410M  Processor. I can move everything to google drive, which i have, so that's fine, I'm using the trial for grive and insync to see which one (insync better but too expensive). I've been speaking to my supervisor and agreed that I could do it in LaTeX and overLeaf for the mean time. 

When I used the VM the computer came to a standstill.

---

### Post by sinqbad on 2018-04-04
> **QIII said:**
> Just by way of a bit of research:

WineHQ has OneDrive rated as "Garbage" and Word 2016 not rated at all.

[Codeweavers rating for Microsoft Office 2016]("https://www.codeweavers.com/compatibility/crossover/microsoft-office-2016") shows OneDrive as 2/5 (probably hardly usable) and Word 2016 as 4/5 (probably usable with some issues).

So, the main thing here is that we need to get you up and running with Word 2016 and OneDrive in the best fashion possible.

btw, thank you for all your help.

---

### Post by monkeybrain20122 on 2018-04-04
> **sinqbad said:**
> paddy@paddy-U36SG:~$ cat /proc/info | grep model
cat: /proc/info: No such file or directory
 
But I just looked up my Laptop and it's Intel®  Core™ i5  2540M/2430M/2410M  Processor. I can move everything to google drive, which i have, so that's fine, I'm using the trial for grive and insync to see which one (insync better but too expensive). I've been speaking to my supervisor and agreed that I could do it in LaTeX and overLeaf for the mean time. 

When I used the VM the computer came to a standstill.

I wonder what kind of Ph.D. degree would mandate students use Office.

---

### Post by QIII on 2018-04-04
sorry.  Typo on my part.  That should have been 

```
cat /proc/cpuinfo | grep model
```

Please post that back.  There are a lot of different models in that series.

If it's a dual core, it may be somewhat strained -- one core for the host and one for the guest.  Windows may want more than that even if each core still supplies two threads.

---

### Post by QIII on 2018-04-04
> **monkeybrain20122 said:**
> I wonder what kind of Ph.D. degree would mandate students use Office.

Does that matter in the context of this discussion?  Let's worry about what the OP is asking for help with.

---

### Post by SeijiSensei on 2018-04-04
> **sinqbad said:**
> When I used the VM the computer came to a standstill.

How much memory do you have?  I use VirtualBox on machines with 4 GB of RAM and greater.  Usually Windows runs fine in a 2 GB VM.  On a 4 GB machine, I'd allocate 1.5 GB for the host Linux system and 2.5 GB for Windows.

An i5 is more than powerful enough to run VMs.  The memory is usually the limiting factor.  You don't want the VM to be so starved for memory that it needs to swap to disk.

---

### Post by QIII on 2018-04-05
I have the Win 10 VM on this machine running on one core (two threads), but I have given it 4GB of RAM.  It runs just fine.

---

### Post by zoomspeed on 2018-04-06
There are WS office that is very similar with MS office,you can use it

---

### Post by QIII on 2018-04-06
As mentioned earlier, the OP is not interested in an alternative to MS products.

---

