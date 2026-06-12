---
title: "Problem trying to use Thunderbird profile on xp box"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by naggis on 2008-06-04
My files are located on an xp desktop which is also used as a file server for my laptop which is dual booted xp and Hardy. I am trying to use a common profile for Thunderbird based on the one located on the xp box. When I try to create the required profile to work on Hardy using thunderbird -profilemanager, there is an error report as shown below -
** (gecko:6313): WARNING **: Operation not supported by backend
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 438 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
I am still a ubuntu newbie and non too familiar with the use of terminals and commands, can anyone tell me what I am doing wrong please.
Hardy seems to support NTFS so that should not be a problem. Is it perhaps that using a profile located on another machine is a no no?
Any guidance would be great.
Thanks

---

### Post by naggis on 2008-06-04
bump

---

### Post by kellemes on 2008-06-04
Could be you don't have read/write permission on the xp-box maybe?
Can you confirm this?

---

### Post by naggis on 2008-06-04
Yes I do have the permission. I think the problem must be with the profilemanager not accepting files from a networked computer. But how to prove this and how to get round the problem.
It works if I copy the profiles from the xp server to the laptop but then the copied profile is not up to date if changes have been made on the xp box. Then I am into the complication of synchronising the two profiles - and that isn't the most reliable process.

---

### Post by kellemes on 2008-06-04
> **naggis said:**
> Yes I do have the permission. I think the problem must be with the profilemanager not accepting files from a networked computer. But how to prove this and how to get round the problem.
It works if I copy the profiles from the xp server to the laptop but then the copied profile is not up to date if changes have been made on the xp box. Then I am into the complication of synchronising the two profiles - and that isn't the most reliable process.

Myself, I'm using a separate partition I share between XP and Linux (setup as dual-boot). So I don't need any networking to share the profile-folder. Maybe an idea?
Anyway, I'm rather ignorant with networking related stuff, so I'm afraid I can't help with your specific issue, sorry.

---

### Post by naggis on 2008-06-05
Like you, I can see the mozilla profiles for both of the dual booted systems. But what I want to do is have a single profile somewhere which will apply to the mozilla software whichever computer I am using - either my xp desktop or the dual booted xp/ubuntu laptop. It seem that such a system would be straight forward as you can set up different profiles for mozilla. But for some reason the -profilemanager will not allow me to use the profile folders that are located on the xp box across the network.
Just a thought, could this be anything to do with using a wireless network (which I am)?

---

### Post by kellemes on 2008-06-06
> **naggis said:**
> Like you, I can see the mozilla profiles for both of the dual booted systems. But what I want to do is have a single profile somewhere which will apply to the mozilla software whichever computer I am using - either my xp desktop or the dual booted xp/ubuntu laptop. It seem that such a system would be straight forward as you can set up different profiles for mozilla. But for some reason the -profilemanager will not allow me to use the profile folders that are located on the xp box across the network.
Just a thought, could this be anything to do with using a wireless network (which I am)?

Like I said, I'm not the brightest with networks..
I hope someone else has a bright idea ;-)

---

### Post by naggis on 2008-06-06
So do I. Thanks for your reply anyway.

---

### Post by ruffEdgz on 2008-06-06
Well, I got the same error when I changed the name of the 'default' profile I set up for my IMAP account then tried to run Thunderbird. I changed the profile name back to default and it worked. 

I'm wondering if you made a brand new profile through the command
```

thunderbird -profilemanager

```
or just changed the name of the default profile to something else and tried running it?

Just a thought :D

---

### Post by naggis on 2008-06-06
I have created new profiles. The method used has worked when working with the dual booted xp and Hardy on the laptop. So I am reasonable happy with that method.
Did you use a single profile for use by firefox on two separate wireless connected computers?
It seems that the profilemanager would not accept trying to use a profile located on another (xp) computer.

---

### Post by ruffEdgz on 2008-06-06
Not on my laptop, no but that is something to try. 

I will try placing a centralized profile on my windows machine and see if I can connect to that profile as well. I can see this working but it's hard to know the network settings for where this is taking place ;)

I could see linking the server file from your server location to your ~/.mozilla/firefox/ folder. Let me try something and see if it works :D

---

### Post by naggis on 2008-06-06
It will be interesting to see if profilemanager gives you the same error messages. I used the original folder in xp Documents and Settings and shared it across the network. I did also try creating a separate folder on a separate drive on the xp machine - all with the same result - a no no.

---

### Post by cariboo on 2008-06-06
I don't really recommend this, but if you share your complete windows hard drive and get to mount on ubuntu startup you could probably create a symlink from where your profile is located on your windows partiton to ~/.mozilla-thunderbird. Remember the the mail storage directory has to be named exactly the same on both computers. TO create a symlink in a terminal type:

```
ln -s /media/windows/path-to-thunderbird-profile.ini /home/user/.mozilla-thunderbird/profile.ini
```

OF course you will have to change the path /media/windows/path-to-thunderbird-profile.ini to where ever your windows partition is mounted and change the user in  /home/user/.mozilla-thunderbird/profile.ini to your user name.

It would probably a lot easier to use something like Gmail and have the emails forwarded to your email address.

Good Luck

Jim

---

### Post by naggis on 2008-06-06
You have given me a few things to think about there - thanks. It might take some effort to sort all the possibilities.

---

### Post by ruffEdgz on 2008-06-06
> **cariboo907 said:**
> I don't really recommend this, but if you share your complete windows hard drive and get to mount on ubuntu startup you could probably create a symlink from where your profile is located on your windows partiton to ~/.mozilla-thunderbird. Remember the the mail storage directory has to be named exactly the same on both computers. TO create a symlink in a terminal type:

```
ln -s /media/windows/path-to-thunderbird-profile.ini /home/user/.mozilla-thunderbird/profile.ini
```

OF course you will have to change the path /media/windows/path-to-thunderbird-profile.ini to where ever your windows partition is mounted and change the user in  /home/user/.mozilla-thunderbird/profile.ini to your user name.

It would probably a lot easier to use something like Gmail and have the emails forwarded to your email address.

Good Luck

Jim

That is exactly wait I'm trying right now and it works to a degree.

First, I created a new profile in firefox, then I mounted a windows server to my computer like so:
```

 mount -t cifs -o username=myUser,password=myPass //servername/shareFolder /mnt/samba

```
** you will have to change some things to make it work for you*

I then transferred the profile from my linux machine to the server:
```

cp -rf ~/.mozilla/firefox/1pcczkzq.ProfileName/ /mnt/samba/

```

Once complete, delete the file that is on your linux box:
```

rm -rf ~/.mozilla/firefox/1pcczkzq.ProfileName/

```

After that is complete, you can create a symlink from the mounted windows drive to the firefox folder:
```

ln -sdf /mnt/samba/1pcczkzq.ProfileName/ ~/.mozilla/firefox/

```

After that is complete, if you wish to have the windows mount to start up every time, you must place it in the /etc/fstab file:
```

cp /etc/fstab /etc/fstab.bk

vi /etc/fstab

```

Place at the bottom of the fstab file:
```

//servername/shareFolder /mnt/samba cifs username=myUser,password=myPass 0 0

```
** this should be just like the mount command from above were you change some things to make it work for you.*

Make sure to go back into the terminal and into firefox -profilemanager and make sure "Don't ask at Startup" isn't checked so it will ask you to pick the profile of your choice.

It worked for the firefox and it should work for the thunderbird but the files will be different (~/.mozilla-thunderbird/) but the idea is the same.

I found that the profile that I made isn't perfect when I start it up and I think it has something to do with the permissions. If I start up firefox from the terminal with 'sudo', it works fine. If I start it up regularly from the menu, it doesn't work as well. Don't know if it's because of the symlink or the profile just not being correct but it kind of works :D

Hope this helps!

---

### Post by naggis on 2008-06-06
Ruffedgz. Thanks for that. No doubt my mentioning that I had used profilemanager made you think that I am fully familiar with the use of code. Well, I am but a newbie really, having used Ubuntu of a couple of months only. However, one of the reasons for giving it a try was to move the grey matter a bit. So I will look very closely at what you say and attempt to understand and make it work. It is good to know that it does work for you and that it should for me if I keep at it
Will report back - but maybe not today!!!

---

