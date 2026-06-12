---
title: "properties"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-06-02
On start up the  T-Bird
 mail notification  properties window opens on the desk top.

How to stop that?

---

### Post by traditionalist on 2012-06-02
> **rosswmcgee said:**
> On start up the  T-Bird
 mail notification  properties window opens on the desk top.

How to stop that?

Take it out of autostart. Or configure Thunderbird to start "silent";

[[IMG]http://img692.imageshack.us/img692/4066/thunderbirdpreferences0.th.png[/IMG]](http://img692.imageshack.us/i/thunderbirdpreferences0.png/)

---

### Post by rosswmcgee on 2012-06-02
Ignorant on how to that.

---

### Post by traditionalist on 2012-06-02
> **rosswmcgee said:**
> Ignorant on how to that.

Do you want to prevent it starting automatically?  Or would you like to configure it to do something else?

Tell me what you want and we can try to set it up as you want it.

---

### Post by rosswmcgee on 2012-06-02
T-bird appears on my panel and is ready when I want to check mail. For some reason

recently the notification properties window opens on the desk top, which it never did before. I am happy with T-Bird being on the panel and opening it when I wish to.

---

### Post by traditionalist on 2012-06-02
> **rosswmcgee said:**
> T-bird appears on my panel and is ready when I want to check mail. For some reason

recently the notification properties window opens on the desk top, which it never did before. I am happy with T-Bird being on the panel and opening it when I wish to.

That may be the result of an update. Can you post a screenshot of the panel you do not wish to open when Thunderbird launches...............

---

### Post by rosswmcgee on 2012-06-02
the window says general, status icon,message pop ups

I have a screen shot but do no know how to post it.

---

### Post by traditionalist on 2012-06-02
> **rosswmcgee said:**
> file:///home/rosswmcgee/Desktop/Screenshot%20from%202012-06-02%2015:37:46.png

Hope that works! the window says general, status icon,message pop ups

That file is located on your machine, you have not uploaded it anywhere.

To upload it, click on "manage attachments" at the bottom of your posting window;

[[IMG]http://img859.imageshack.us/img859/1299/selection001i.th.png[/IMG]](http://img859.imageshack.us/i/selection001i.png/)

you will get this window and you can upload the file from there;

[[IMG]http://img406.imageshack.us/img406/8342/manageattachmentsubuntu.th.png[/IMG]](http://img406.imageshack.us/i/manageattachmentsubuntu.png/)

---

### Post by traditionalist on 2012-06-02
I think all you have to do in this case is uncheck the relevant boxes in the screen shown.

I have posted a full size screen here ( instead of a thumbnail), with the relevant boxes outlined in red;

[[IMG]http://img138.imageshack.us/img138/4066/thunderbirdpreferences0.png[/IMG]](http://img138.imageshack.us/i/thunderbirdpreferences0.png/)

You can't do anything wrong. If you uncheck the wrong box for instance, you can just check it again.

---

### Post by rosswmcgee on 2012-06-02
> **traditionalist said:**
> That file is located on your machine, you have not uploaded it anywhere.

To upload it, click on "manage attachments" at the bottom of your posting window;

[[IMG]http://img859.imageshack.us/img859/1299/selection001i.th.png[/IMG]](http://img859.imageshack.us/i/selection001i.png/)

you will get this window and you can upload the file from there;

[[IMG]http://img406.imageshack.us/img406/8342/manageattachmentsubuntu.th.png[/IMG]](http://img406.imageshack.us/i/manageattachmentsubuntu.png/)
Sorry I do not see  manage attachments

---

### Post by traditionalist on 2012-06-02
> **rosswmcgee said:**
> Sorry I do not see  manage attachments

They are here;

[[IMG]http://img600.imageshack.us/img600/5694/selection001mu.png[/IMG]](http://img600.imageshack.us/i/selection001mu.png/)

---

### Post by rosswmcgee on 2012-06-02
I do not know what your example is. What is it?

---

### Post by Curtis6767 on 2012-06-02
> **rosswmcgee said:**
> I do not know what your example is. What is it?

When you hit "New Reply" it opens up the dialog box. At the top of the box you will see all kinds of little icons.

In the upper row, next to the little smiley face, there is a paper clip. Click on that paper clip and another box will open. Select browse and search your computer for the image you want to post.

Hope this helps

---

### Post by rosswmcgee on 2012-06-02
I do not see new reply, the icons on this quick reply have no smiley face or paper clip.

---

### Post by Curtis6767 on 2012-06-02
> **rosswmcgee said:**
> I do not see new reply, the icons on this quick reply have no smiley face or paper clip.

Don't use the Quick Reply.

Look down on the lower left of this thread and you will see "New Reply."

Click on that and then look for the paper clip icon. Click on that and then select Browse.

Search your files for the image you're trying to post and then click Upload.

Hope this helps.

---

### Post by rosswmcgee on 2012-06-02
Thanks here is what keeps popping up on start up.

---

### Post by Curtis6767 on 2012-06-02
Ross, I don't use Thunderbird so can't help you with that, but now that you've got the image loaded, then maybe traditionalist or someone else can take it from here.

Goodnight.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> Thanks here is what keeps popping up on start up.

That is an indicator applet.  You can get rid of it by deleting this;

/usr/share/indicators/messages/applications/**thunderbird**

---

### Post by rosswmcgee on 2012-06-03
How do I find that file? I put the string in file search not there?

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> How do I find that file? I put the string in file search not there?


that is the location in the file system;

/usr/share/indicators/messages/applications/[B]thunderbird

[[IMG]http://img855.imageshack.us/img855/6465/selection001m.th.png[/IMG]](http://img855.imageshack.us/i/selection001m.png/)


[/B]

---

### Post by rosswmcgee on 2012-06-03
found file will not allow delete

---

### Post by oldos2er on 2012-06-03
Since it's outside of your home folder you need to use sudo: ```
sudo rm /usr/share/indicators/messages/applications/thunderbird
```

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> found file will not allow delete

Did you manage to delete it?  Problem solved?

---

### Post by rosswmcgee on 2012-06-03
rosswmcgee@rosswmcgee-EL1330:~$ sudo rm /usr/share/indicators/messages/applications/thunderbird
[sudo] password for rosswmcgee: 
rosswmcgee@rosswmcgee-EL1330:~$ sudo rm /usr/share/indicators/messages/applications/thunderbird
rm: cannot remove `/usr/share/indicators/messages/applications/thunderbird': No such file or directory
rosswmcgee@rosswmcgee-EL1330:~$

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> rosswmcgee@rosswmcgee-EL1330:~$ sudo rm /usr/share/indicators/messages/applications/thunderbird
[sudo] password for rosswmcgee: 
rosswmcgee@rosswmcgee-EL1330:~$ sudo rm /usr/share/indicators/messages/applications/thunderbird
rm: cannot remove `/usr/share/indicators/messages/applications/thunderbird': No such file or directory
rosswmcgee@rosswmcgee-EL1330:~$

Are you the administrator on this machine?  Did you set it up?

---

### Post by rosswmcgee on 2012-06-03
I set it up on home desktop. tbird did not do this untill recently. Just a guess Is it possible thunderbird at the end of the sudo is not supposed to be there?

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> I set it up on home desktop. tbird did not do this untill recently. Just a guess Is it possible thunderbird at the end of the sudo is not supposed to be there?

what this does ( should do!), is delete the indicator message applet for thunderbird, so it has to be specified.  This indicator applet is what is popping up the panel you see.

---

### Post by rosswmcgee on 2012-06-03
If I go to :

usr/share/indicators/messages/applications/


There is no Thunderbird when I open the applications folder.

Now there is no mail. Will try re-install Tbird

---

### Post by traditionalist on 2012-06-03
OK. Let's try something else.

Go to Thunderbird add-ons manager;

[[IMG]http://img832.imageshack.us/img832/7925/addonsmanagermozillathu.th.png[/IMG]]("http://img832.imageshack.us/i/addonsmanagermozillathu.png/")

On the "Messaging Menu and Unity Launcher Integration 0.93"  click on "Disable". You should get this;

[[IMG]http://img6.imageshack.us/img6/63/selection001f.th.png[/IMG]](http://img6.imageshack.us/i/selection001f.png/)


Restart Thunderbird.

Does this solve your problem?

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> If I go to :

usr/share/indicators/messages/applications/


There is no Thunderbird when I open the applications folder.

Now there is no mail. Will try re-install Tbird

Try what I just posted first.  That should disable the applet.

Sorry, but I am not sure I understand you correctly, "Now there is no mail", do you mean you have lost Thunderbird?

---

### Post by rosswmcgee on 2012-06-03
re-installed Tbird working fine, followed the new directions in msg mgr. did not fix the problem.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> re-installed Tbird working fine, followed the new directions in msg mgr. did not fix the problem.

What "msg mgr"?

---

### Post by rosswmcgee on 2012-06-03
On the "Messaging Menu and Unity Launcher Integration 0.93" click on "Disable". You should get this, I did this.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> On the "Messaging Menu and Unity Launcher Integration 0.93" click on "Disable". You should get this, I did this.

Well, sorry, but I can't think of anything else to try. maybe somebody else will come up with a way to disable that applet.

I would like to know how you "lost" Thunderbird.  That does not sound good, but maybe that is something for another time.

---

### Post by rosswmcgee on 2012-06-03
When I clicked on it the drop down menu had no mail, everything else was there. Re-install and it was back working fine. Thanks for trying, it is only a minor annoyance. 
I keep thinking that the popup itself should have an option but do not see it yet. At least I learned how to upload a png. So all was not lost.

---

### Post by rosswmcgee on 2012-06-03
fixed it!!!!!!!!!!!!!!!! 

The problem had nothing to do with Tbird. I removed tbird still had problem/
re-installed tbird. Removed "mail- notification" in synaptic. Problem solved.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> fixed it!!!!!!!!!!!!!!!! 

The problem had nothing to do with Tbird. I removed tbird still had problem/
re-installed tbird. Removed "mail- notification" in synaptic. Problem solved.

Excellent!  Well done! It never occurred to me that you might be using another notifier! ( Slaps forehead ruefully!)

---

### Post by rosswmcgee on 2012-06-03
Thanks for all your help. I also tried going to gconf-editor, to no avail. 

Patience has been a reward in the Linux world. To often folks get exasperated and give

up.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> Thanks for all your help. I also tried going to gconf-editor, to no avail. 

Patience has been a reward in the Linux world. To often folks get exasperated and give

up.

True enough, patience and perseverance pay off.

On another note, and since you are obviously setting your e-mail up as you like it, you might like to try this;

[http://www.firetrust.com/en/products/mailwasher-pro](http://www.firetrust.com/en/products/mailwasher-pro)

[http://www.mailwasher.net/](http://www.mailwasher.net/)  ( Free version)

I used it for years on Windows ( I got a lifetime licence from the developer as a beta tester), and I was very sad not to have it any more on Linux.

Just out of curiosity, and because I had to install Wine for something else, I gave my old version a try,  I just copied the windows  .exe file to my Ubuntu box, clicked on it, and joy of joys! It runs perfectly.

I am very happy indeed about that.  All the spam and other stuff never even gets to my machine now, it is deleted on the provider server!

It is said that "all things come to he who waits".  Who knows what will turn up in future?

Anyway, I thought I would mention it because it saves a lot of trouble, and is also better security. It is running in my system tray as I write. Blinks unobtrusively when I get a mail. If It's "known" spam it just gets deleted, if it's "unknown" spam a simple click deletes it, and I never even have to open my mail program.

Just thought you might like to know.

As I understand it the free version only allows one mail account,   the Pro version allows as many as you like. For a lot of people the free version will be enough.

---

### Post by rosswmcgee on 2012-06-03
I get most of my email through Opera. I use Tbird to work with Libre as it syncs

spreadsheets. I cannot use wine because I have no windows install discs. Every computer

I ever bought I just erased it with a Distro clean install. Windows 8 reviews are not

so hot. People do not like change. When I first tried 11.10 I did not like it. Removed it then installed Mint debian. Then my wife got a smartphone and Mint would
not mount it so I went back to Ubuntu 11.10 and it did. So then I installed 12.04
on my wifes Mint 9, and upgraded this computer to 12.04 from 11.10.
I have another computer running Debian Squeeze and it is fine but now that I 
am used to Ubuntu 12.04 I prefer it. Who would a thunk that would happen. 
I may be wrong but when I check the Distro watch and see that Mint is in the lead by
two times, I just think people just have a hard time adjusting to something new. 

The next Ubuntu release I may try on my Debian computer, but will leave the 2 12.04 lts machines alone.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> I get most of my email through Opera. I use Tbird to work with Libre as it syncs

spreadsheets. I cannot use wine because I have no windows install discs. Every computer

I ever bought I just erased it with a Distro clean install. Windows 8 reviews are not

so hot. People do not like change. When I first tried 11.10 I did not like it. Removed it then installed Mint debian. Then my wife got a smartphone and Mint would
not mount it so I went back to Ubuntu 11.10 and it did. So then I installed 12.04
on my wifes Mint 9, and upgraded this computer to 12.04 from 11.10.
I have another computer running Debian Squeeze and it is fine but now that I 
am used to Ubuntu 12.04 I prefer it. Who would a thunk that would happen. 
I may be wrong but when I check the Distro watch and see that Mint is in the lead by
two times, I just think people just have a hard time adjusting to something new. 

The next Ubuntu release I may try on my Debian computer, but will leave the 2 12.04 lts machines alone.

You don't need any install disks. Just download the application and start it. You can get it from lots of places;

[http://www.winehq.org/](http://www.winehq.org/)


For the Mailwasher you just need to download the Windows executable and run it.

[http://www.mailwasher.net/](http://www.mailwasher.net/)

---

### Post by rosswmcgee on 2012-06-03
Wine can be installed from software mgr. correct. I've done that but always get a place where it says select system, so I select xp as an  example then I get to a place 
where it says install discs. So since I have no discs I just uninstalled wine and forgot about it.

---

### Post by traditionalist on 2012-06-03
> **rosswmcgee said:**
> Wine can be installed from software mgr. correct. I've done that but always get a place where it says select system, so I select xp as an  example then I get to a place 
where it says install discs. So since I have no discs I just uninstalled wine and forgot about it.

Well, I have never needed anything like that. I just installed Wine and that was it. I did not have to configure anything at all.

I just click on a Windows .exe file and it either runs or it doesn't.  Quite a few run very well.

---

