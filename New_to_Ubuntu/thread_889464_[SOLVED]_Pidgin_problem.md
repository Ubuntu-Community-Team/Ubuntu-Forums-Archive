---
title: "[SOLVED] Pidgin problem"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-14
I'm not sure if this thread should go here, if there's a better resource for my question to be answered, please link me there.

I couldn't log in with my MSN account. That's it.

This is what I did:

Protocol: MSN
Screen name: <my email>@gmail.com (I use a Gmail account for MSN)
Password: <duh>
Local alias: <I left this blank.>

I didn't change any of the advance settings.

And this is what Pidgin gave me: [my account] disconnected. Connection error from Notification server: unable to connect. Then there are two options, one that says modify account and the other says reconnect. Everytime I click reconnect, the same error message appears. What should I do? So far I haven't been able to sign in even once.

---

### Post by iaculallad on 2008-08-14
> **zzzonked said:**
> 
This is what I did:

**Protocol: MSN**
Screen name: <my email>@gmail.com (I use a Gmail account for MSN)
Password: <duh>
Local alias: <I left this blank.>


Change your protocol to **XMPP** instead, not MSN.

---

### Post by Tom--d on 2008-08-14
Update to the lastest Pidgin. 
Enable Ubuntu Backports in System > admin >software ... 

This will let you update it to the newest one.

MSN recently changed its servers. Thus making emesene, amsn and Pidgin to not work with MSN. They have all been updated and now work. :)

---

### Post by tangibleorange on 2008-08-14
> **zzzonked said:**
> I'm not sure if this thread should go here, if there's a better resource for my question to be answered, please link me there.

I couldn't log in with my MSN account. That's it.

This is what I did:

Protocol: MSN
Screen name: <my email>@gmail.com (I use a Gmail account for MSN)
Password: <duh>
Local alias: <I left this blank.>

I didn't change any of the advance settings.

And this is what Pidgin gave me: [my account] disconnected. Connection error from Notification server: unable to connect. Then there are two options, one that says modify account and the other says reconnect. Everytime I click reconnect, the same error message appears. What should I do? So far I haven't been able to sign in even once.

go to your MSN account in Pidgin (in the Accounts Menu) and select 'Edit Account'. Click on the advanced tab. Where it says GNOME proxy settings, change it to 'no proxy' and save (assuming you don't use a proxy). Also could you make sure 'use HTTP method' is unchecked and that:
the server is:messenger.hotmail.com
the port is:1863

---

### Post by zzzonked on 2008-08-14
Still couldn't work. Should it look like this?

Protocol: XMPP
Screen name: <my Google ID>
Domain: gmail.com
Resource: Home
Password: <password>
Local alias: <blank>

Same error message.

Any boxes I should check or uncheck, or fields I should fill up/edit?

---

### Post by zzzonked on 2008-08-14
> **Tom--d said:**
> Update to the lastest Pidgin. 
Enable Ubuntu Backports in System > admin >software ... 

This will let you update it to the newest one.

MSN recently changed its servers. Thus making emesene, amsn and Pidgin to not work with MSN. They have all been updated and now work. :)

Err... how do you enable Ubuntu Backports? I clicked system > admin > software sources, but I don't see anything that says backports...

---

### Post by iaculallad on 2008-08-14
> **zzzonked said:**
> Still couldn't work. Should it look like this?

Protocol: XMPP
Screen name: <my Google ID>
Domain: gmail.com
Resource: Home
Password: <password>
Local alias: <blank>

Same error message.

Any boxes I should check or uncheck, or fields I should fill up/edit?

Screen name **should only contain your Username**, that's excluding the @ sign and gmail.com (@gmail.com)

Protocol: XMMP

---

### Post by Tom--d on 2008-08-14
> **zzzonked said:**
> Err... how do you enable Ubuntu Backports? I clicked system > admin > software sources, but I don't see anything that says backports...

Updates.. its in the tabs.

---

### Post by zzzonked on 2008-08-14
> **Tom--d said:**
> Updates.. its in the tabs.

Unsupported updates (hardy-backports)? I've saved that, then now I have a whole list of stuff to update, should I just check the Pidgin ones, or just update all of them?

---

### Post by Tom--d on 2008-08-14
> **zzzonked said:**
> Unsupported updates (hardy-backports)? I've saved that, then now I have a whole list of stuff to update, should I just check the Pidgin ones, or just update all of them?

Your choice.

IF you only require Pidgin. Install Pidgin.
Thos updates are 'normally' just updating software to the lastest one. 
For example, 
Trasmission is updated to 1.22 (from 1.06)

---

### Post by zzzonked on 2008-08-14
Done. Downloaded everything. Turned Pidgin off and on again, same error message :(

---

### Post by Lod on 2008-08-14
> **zzzonked said:**
> What should I do? So far I haven't been able to sign in even once.Have you ever signed in before with the account? Or do you mean only with Pidgin?

> **iaculallad said:**
> Screen name **should only contain your Username**, that's excluding the @ sign and gmail.com (@gmail.com)

Protocol: XMMPI use the MSN protocol with my full address, no problems with connecting.

---

### Post by zzzonked on 2008-08-14
I've been able to sign in using Windows Live Messenger for the past 2 years back when I was still on Vista. Now this is killing me. Is there another IM program that works in Ubuntu? Pidgin is really getting on my nerves now :(

---

### Post by Lod on 2008-08-14
Try emesene then, it looks almost like the MSN Messenger from Microsoft. It's in the repositories.

---

### Post by Tom--d on 2008-08-14
> **zzzonked said:**
> I've been able to sign in using Windows Live Messenger for the past 2 years back when I was still on Vista. Now this is killing me. Is there another IM program that works in Ubuntu? Pidgin is really getting on my nerves now :(

Yeah,

Go to [www.emesene.org](www.emesene.org) and download the source code. Just open it up and double click the file emesene. Done!

It is in the repos but its out of date and doesn't work with MSN servers any more. 
New one does :D

Or you can download the .deb here, 

[http://www.getdeb.net/search.php?keywords=emesene](http://www.getdeb.net/search.php?keywords=emesene)

but I dont know how its been compiled.

---

### Post by Lod on 2008-08-14
> **Tom--d said:**
> Yeah,
and doesn't work with MSN servers any more. 
New one does :DIt doesn't? Yesterday morning (CET) I used it for the last time.

It's getting a bit strange though. I couldn't login with aMSN for the last 2 weeks. It seems Pidgin isn't working anymore. Then you say emesene doesn't work anymore... Is Microsoft up to something?:popcorn:

---

### Post by Tom--d on 2008-08-14
> **Lod said:**
> It doesn't? Yesterday morning (CET) I used it for the last time.

It's getting a bit strange though. I couldn't login with aMSN for the last 2 weeks. It seems Pidgin isn't working anymore. Then you say emesene doesn't work anymore... Is Microsoft up to something?:popcorn:

Yeah... >.>

But **Emesene 1.01 source code** works for me.

---

### Post by zzzonked on 2008-08-14
> **Tom--d said:**
> Yeah,

Go to [www.emesene.org](www.emesene.org) and download the source code. Just open it up and double click the file emesene. Done!

It is in the repos but its out of date and doesn't work with MSN servers any more. 
New one does :D

Or you can download the .deb here, 

[http://www.getdeb.net/search.php?keywords=emesene](http://www.getdeb.net/search.php?keywords=emesene)

but I dont know how its been compiled.

I tried double clicking the file named emesene and it gave me this in gedit:
#!/usr/bin/env python
# -*- coding: utf-8 -*-

#   This file is part of emesene.
#
#    Emesene is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    emesene is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with emesene; if not, write to the Free Software
#    Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

try:
    # Change the process name.
    import ctypes
    libc = ctypes.CDLL('libc.so.6')
    libc.prctl(15, 'emesene', 0, 0)
except:
    pass

try:
    from emesene import Controller
except ImportError:
    import Controller

Controller.main()

Something wrong?

---

### Post by zzzonked on 2008-08-14
Is this what I'm supposed to type in terminal to install emesene?

sudo apt-get install emesene

I'm just guessing, never done this before.

---

### Post by tangibleorange on 2008-08-14
> **zzzonked said:**
> Is this what I'm supposed to type in terminal to install emesene?

sudo apt-get install emesene

I'm just guessing, never done this before.

yeah that's correct. you'll never guess what though - my pidgin just locked me out with the same error as you! must be MS doing something :confused:

---

### Post by Dougie187 on 2008-08-14
Just so you know. After you update to the newest pidgin (and even before) Do not use XMPP protocol for MSN. If you use that one, you need the "host" but that protocol is what Google Talk uses. Either way, if you want to log into MSN you want to stick with the MSN plugin.

For installing software, if you are unsure what the package name is but you have an idea, you can type the following in the terminal to get a list of relavent package names.
```
apt-cache search *packagename*
```
Here packagename would be replaced with emesene. Then you can pick the package from that list you want to install (with a description similar to what you are looking for) and then type
```
sudo apt-get install *programname*
```
where programname is replaced with the name that you got from the previous command.

However, in this case, the code that you gave should be right. so you want to type
```
sudo apt-get install emesene
```
in a terminal. Also, you can look for the package in synaptic.

---

### Post by Tom--d on 2008-08-14
> **zzzonked said:**
> I tried double clicking the file named emesene and it gave me this in gedit:
#!/usr/bin/env python
# -*- coding: utf-8 -*-

#   This file is part of emesene.
#
#    Emesene is free software; you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation; either version 2 of the License, or
#    (at your option) any later version.
#
#    emesene is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with emesene; if not, write to the Free Software
#    Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

try:
    # Change the process name.
    import ctypes
    libc = ctypes.CDLL('libc.so.6')
    libc.prctl(15, 'emesene', 0, 0)
except:
    pass

try:
    from emesene import Controller
except ImportError:
    import Controller

Controller.main()

Something wrong?

Nono

Run the file!
double click it. and click run. Simple!

---

### Post by zzzonked on 2008-08-14
Guess I just chose the best time to install Ubuntu -.-"

---

### Post by Tom--d on 2008-08-14
> **Dougie187 said:**
> Just so you know. After you update to the newest pidgin (and even before) Do not use XMPP protocol for MSN. If you use that one, you need the "host" but that protocol is what Google Talk uses. Either way, if you want to log into MSN you want to stick with the MSN plugin.

For installing software, if you are unsure what the package name is but you have an idea, you can type the following in the terminal to get a list of relavent package names.
```
apt-cache search *packagename*
```
Here packagename would be replaced with emesene. Then you can pick the package from that list you want to install (with a description similar to what you are looking for) and then type
```
sudo apt-get install *programname*
```
where programname is replaced with the name that you got from the previous command.

However, in this case, the code that you gave should be right. so you want to type
```
sudo apt-get install emesene
```
in a terminal. Also, you can look for the package in synaptic.

The package in the repos is OUT OF DATE and doesnt work.

You need the emesene 1.01
In the repos is emesene 1.0

---

### Post by tangibleorange on 2008-08-14
> **Tom--d said:**
> The package in the repos is OUT OF DATE and doesnt work.

You need the emesene 1.01
In the repos is emesene 1.0

the emesene i got from getdeb just locks up when i try and connect. the debug in the console shows everything timing out...
mind you the one from the repos doesn't work either

---

### Post by zzzonked on 2008-08-14
> **Tom--d said:**
> Nono

Run the file!
double click it. and click run. Simple!

But there wasn't a Run option for me to click on in the first place, it just launched itself in gedit. But it's okay I've already got emesene installed, only thing is I still can't log in :(

---

### Post by Dougie187 on 2008-08-14
Did you try the new pidgin without XMPP for MSN? I am currently connected using Pidgin and MSN.

---

### Post by zzzonked on 2008-08-14
> **Tom--d said:**
> Nono

Run the file!
double click it. and click run. Simple!

Okay I downloaded emesene-1.0.1.tar.gz. Double click, it opened in archive manager. Double click again, a long list of files and folders. I scroll down till I see a file called emesene, size 1 KB, type unknown, I double click that, it automatically gets launched in gedit. What's wrong now?

Dammit, why is it such a pain just to get an IM program working :(

---

### Post by Tom--d on 2008-08-14
> **zzzonked said:**
> Okay I downloaded emesene-1.0.1.tar.gz. Double click, it opened in archive manager. Double click again, a long list of files and folders. I scroll down till I see a file called emesene, size 1 KB, type unknown, I double click that, it automatically gets launched in gedit. What's wrong now?

Dammit, why is it such a pain just to get an IM program working :(

Nonononono

You need to extract the archive.
Right click the .tar.gz then Extract here.

Then locate the emesene file in the folder.
double click it. then Run
Easy :d

---

### Post by tangibleorange on 2008-08-14
> **zzzonked said:**
> Okay I downloaded emesene-1.0.1.tar.gz. Double click, it opened in archive manager. Double click again, a long list of files and folders. I scroll down till I see a file called emesene, size 1 KB, type unknown, I double click that, it automatically gets launched in gedit. What's wrong now?

Dammit, why is it such a pain just to get an IM program working :(

get the file from here: [http://www.getdeb.net/app/emesene](http://www.getdeb.net/app/emesene)

then when firefox asks what to do, select run as GDebi Package Installer. It should be fairly straightforward from there.

---

### Post by Tom--d on 2008-08-14
> **tangibleorange said:**
> get the file from here: [http://www.getdeb.net/app/emesene](http://www.getdeb.net/app/emesene)

then when firefox asks what to do, select run as GDebi Package Installer. It should be fairly straightforward from there.

that one doesnt work for me either. 

Thats why I use the source. (its more up to date)

No need to compile either. 
Just run the emesene file. Simple.

Just move the folder where ever you want. (I put mine in /use/share/emesene) and made a launcher in my menu.

The launcher consisted of.

/use/share/emesene/emesene

Done, thats the shortcut :)
All the configuration files are in /home/yourusename/.config/emesene1.0

---

### Post by zzzonked on 2008-08-14
> **Tom--d said:**
> Nonononono

You need to extract the archive.
Right click the .tar.gz then Extract here.

Then locate the emesene file in the folder.
double click it. then Run
Easy :d

Actually I managed to realize this after posting my post and before reading yours :p and now I'm FINALLY connected. But this is only because I checked the use HTTP option, I receive an error message when I try to login "normally". Why is this so and what's the difference between the 2?

---

### Post by Tom--d on 2008-08-14
> **zzzonked said:**
> Actually I managed to realize this after posting my post and before reading yours :p and now I'm FINALLY connected. But this is only because I checked the use HTTP option, I receive an error message when I try to login "normally". Why is this so and what's the difference between the 2?

I use the non http. http is just using the port 80 (correct me if im wrong).

I think it maybe how you are connected to the internet.
How are you connected?

if it works for you. Keep it :P

---

### Post by zzzonked on 2008-08-14
Oh I can't believe it, this is so retarded. I just tried using Pidgin after I succeeded on emesene, and Pidgin worked TOO! (after I checked the use HTTP option, that is...) Okay so now I'm gonna uninstall emesene all over again. I'm supposed to do it at the add/remove thingy right?

---

### Post by tangibleorange on 2008-08-14
```
sudo apt-get purge emesene
```
should do it. you can then delete the source folder also.

---

