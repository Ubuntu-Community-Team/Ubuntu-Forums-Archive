---
title: "All folder content has gone."
date: 2014-01-02
forum: New to Ubuntu
---

### Post by Binman278 on 2014-01-02
My Lubuntu PC has lost the content of all of its folders. I am not sure quite has gone wrong. it might have been me or the PC or both and whilst most of the important stuff was backed up on an external drive I would like the missing bits back. The PC is used stand alone (ie NOT connected to the internet. The operating system is Lubuntu and all I added to it was Cinelerra , Kino and Avidemux for Video editing which it did Exceptionally well.

Here is what happens. Sign in and open "File ManagerPCmanFM". 
Left side of screen under Places I click on the first name (home folder) and it shows all my folders on the right. 
ALL the folders when opened appear empty!
The Rubish bin actually is empty.
At the bottom right of this panel it states "Free Space 14.2 GB (Total 72.8GB). This is what it said when all worked normally. 

So it seems the missing contents are hiding on the hard drive somewhere but where and how can I retrieve them?

Right clicking on a folder & choosing "show hidden folders" doesnt show them.

I am stuck. I dont know what to do but if some body does and can tell me in click by click terms I am able to do that and can copy and paste in the Terminal if need be. I really dont know how I messed this up. It must be contender for Dork of the year award!

---

### Post by Jonathan Precise on 2014-01-02
This also happened to me with Zorin OS 6 Lite (based on Lubuntu 12.04 LTS). I lost all my data. I lost all the programs I had installed.

What Lubuntu version are you using (out of curiosity)?

---

### Post by monkeybrain20122 on 2014-01-02
So if you boot from a live usb and open those folders can you see the content?

---

### Post by Jonathan Precise on 2014-01-02
> **monkeybrain20122 said:**
> So if you boot from a live usb and open those folders can you see the content?

I deleted that Virtual Machine a long time ago.

---

### Post by monkeybrain20122 on 2014-01-02
I am asking op. :)

---

### Post by Dave_L on 2014-01-02
Is it possible that it's only the icons that are not being displayed? Does the file manager have alternate views, such as listing the filenames? Can you view the contents of the folder using the terminal?

---

### Post by monkeybrain20122 on 2014-01-02
> **Dave_L said:**
> Is it possible that it's only the icons that are not being displayed? Does the file manager have alternate views, such as listing the filenames? Can you view the contents of the folder using the terminal?

+1 to terminal. Just open the terminal, navigate to the folder in question , for example, if you want to check your Music folder
```
cd Music
```
then type
```
ls
```

---

### Post by chkneater on 2014-01-02
Also you might want to check the window manager under View and make sure they aren't just 'hidden' by selecting 'view hidden files'

---

### Post by Jonathan Precise on 2014-01-02
> **monkeybrain20122 said:**
> I am asking op. :)

Oh. Oops! :):)

---

### Post by Binman278 on 2014-01-03
Sorry Monkeybrain, I dont quite understand what you mean by booting from a live usb.

If I open the File manager list view and click say on documents it says there are no sub folders. They are about somewhere though as the used hard drive space tells me so.

Then I tried Monkeybrains suggestion with the UX Term terminal. I typed in cd Documents (as this is a sub folder of Didwell my home folder) it came back I didint have permission. So I just typed the next bit anyway ls and got a colourful read out that showed in text form all the folders in the Home folder. A screen shot is hopefully attached. I want to know how to get the contents back from their hiding place now.

Thanks

---

### Post by Dave_L on 2014-01-03
This will provide more detail:

```
ls -l
```

It sounds like the files are still there, and it's merely a problem with the icons not being displayed.

I had a similar issue with xfce, and fixed it by choosing a different theme in Applications Menu >> Settings >> Appearance >> Icons.  But I don't know how that works with lubuntu. Someone else may have a solution.

---

### Post by Binman278 on 2014-01-03
Further to my last reply and having got nowhere with xdg-open either I had moment staring at the pc not knowing really what to do. I am pre PC in age and they just dont teach the proper stuffin schools so my son doesnt know how to fix them. Society just goes to PCWorld buys a pc with Windows and after two years when  the internet has totally screwed it they buy another. Thats a hard world to champion the cause of Ubuntu in. Then I suppose it was God sent St. Linux to me and guided my hand thus:-

Open File Manager and left click on an apparently empty folder to highlight it. 
Go to top of screen and click TOOLS,
Choose Open Current folder as ROOT.
At prompt type in password,
Another File Manager screen opens,
Highlight the same folder and press enter and everything is there as expected and can be opened, moved etc......

Now I am not overly sure what to do next. This ROOT file manager is all the folders and files I expect to see where as the other (Default File Manager) is of little use now. Is there a way to Synchronise them - Amalgamate them, should the default on opening be ROOT? I dont understand why I have sort of Two lots of places where files go or dont.

Sorry If I'm sounding basic here.

Regards

Binman

---

### Post by Dave_L on 2014-01-03
Don't try to move any files.  That's not the problem.

And be very careful with anything you do as ROOT. You can easily make things much worse.

The problem is something to do with the display settings, possibly in the preferences for the normal file manager.

Both instances of the file manager are viewing the same files, but with different access levels.

---

### Post by sotiris2 on 2014-01-03
We really need that ls-l output. I think that somehow he has given away ownership of his folder and has very stict restrictions for 'others' (as in not even being allowed to list files).

---

### Post by Binman278 on 2014-01-03
A Fanfare of Trumpets goes to Dave for pressing the fix it button and a big thank you to the other helpers that got things moving in the right direction. I really do appreciate peoples time and help as without it I would not learn how to make things work and would end up not liking Ubuntu and its lightweight Lubuntu. 

I opened both the default and Root managers and compared the preferences.There are 3, View Content which always seemed set to Anyone. Change Content which always said Only owner or a slight variation on it, But the last box Access Content in the normal default file manager was in all cases saying Nobody but in the Root always said Anybody. So back in the Default I tried changing the Access Content to Anybody, refreshed the screen and low and behold the files appeared. so I tried opening one and it did then I tried to drag it onto a memory stick just inserted and opened in another manager and that worked and could be opened. 

So now I am back in business and can edit video again. I have no idea exactly what caused it/how I managed it, one file I could understand but not the whole lot.

Thanks again

Binman

---

### Post by Impavidus on 2014-01-03
With "access content" (=execute permission) set to owner it should work already. You need the execute permission on directories to browse directory contents. I don't know why the root and non-root file managers gave different output on permissions. Those permissions exist independently of the file manager and should be the same whatever tool you use to view them.

---

