---
title: "Unable to download any package from software center"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by bonedriven on 2012-02-01
Hi, forum!

I have the same problem with the guy in the other thread. But I am not him with a new account...

I have just installed ubuntu in my pendrive and use it in the computer of my workplace. I have set up an automatic proxy.pac in the network settings to get me connected to the internet. Everything works fine so far but I just can't download anything from ubuntu software center, neither can I update this OS. I can download stuff with my browser though.

Thanks!

---

### Post by arochester on 2012-02-01
There are 2 kinds on install on a pendrive. Ordinary is just like a LiveCD and cannot be added to. The other is "persistent" and CAN be added to. Which install have you done?

---

### Post by bonedriven on 2012-02-01
It's persistent. I can download stuff and change stuff in the system. After restart my change is kept.

*EDIT: Now that you have asked, I am not sure. Maybe mine is not a persistent system? I followed [this guide]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/") to create my pendrive ubuntu. I just checked, the casper-rw size is 2gb as I have set. It should be persistent.*

---

### Post by cortman on 2012-02-01
I'll ask you to do the old standby test for most package problems: run

```
sudo apt-get update
```

and post results, so we can see if it actually is connecting to the Ubuntu server mirrors. If it just sits and returns "Waiting for headers..." messages for an hour or more, it's still having problems with your proxy.

---

### Post by bonedriven on 2012-02-01
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) oneiric InRelease
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012) dists/oneiric/main/binary-i386/ Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                              
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg    
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)  

W: Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/dists/oneiric/Release  Unable to find expected entry 'restricted/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)/ oneiric/main i386 Packages (/var/lib/apt/lists/Ubuntu%2011.10%20%5fOneiric%20Ocelot%5f%20-%20Release%20amd64%20(20111012)_dists_oneiric_main_binary-i386_Packages)

---

### Post by cortman on 2012-02-01
Ok, it's definitely not connecting. How did you set up your proxy? And what version of Ubuntu are you using?
I've had the best success setting proxy by going to System Settings>Network>Proxy and editing it there. That's in Gnome shell and Unity, if you're using some other DE it'll be under the network settings, however you get to them.
It could be that your proxy blocks port 21 (FTP), and therefore isn't allowing apt-get to go through.

---

### Post by bonedriven on 2012-02-01
Hi cortman. Thank you.

I am in an institute and a technician helped to set up the proxy for me. Before, I could not connect to internet with this pendrive ubuntu at all. He set a url in the automatic proxy setting (in the format of http:\\*institute domain name*\proxy.pac). It is universally applied (Network->Proxy). I don't know if I'm allowed to give out that proxy address. But can we be sure it's the proxy that's blocking. If that's the case, any way I can get around it? As you see I can download files with my browser very well though.

---

### Post by cortman on 2012-02-01
> **bonedriven said:**
> Hi cortman. Thank you.

I am in an institute and a technician helped to set up the proxy for me. Before, I could not connect to internet with this pendrive ubuntu at all. He set a url in the automatic proxy setting (in the format of http:\\*institute domain name*\proxy.pac). It is universally applied (Network->Proxy). I don't know if I'm allowed to give out that proxy address. But can we be sure it's the proxy that's blocking. If that's the case, any way I can get around it? As you see I can download files with my browser very well though.

Hi!
The way the tech set it up could be all correct, I'm not familiar with setting up proxy that way. How I've done it always is setting the proxy server's IP address, and the port used (usually 80, 81, or 8080 for HTTP). If you know or can find the IP address of your proxy and set it that way, that might do the trick. It's basically the same thing as how it's currently set up, but a different method.
Otherwise, if there's a firewall involved it might be blocking certain ports apt-get uses (80, 21, etc.). If you can find that out that might help deduce the problem further.

---

### Post by bonedriven on 2012-02-03
It's strange in the log that it shows "unable to connect to archive.ubuntu.com IP:91.189.88.40 80" etc. But in the browser I can open those urls and even download packages from the archive.

How do I know if it's the proxy that's blocking?

What can I do about it? Adding hosts file?

[I]EDIT Add: I think I have the same problem with [this guy]("http://ubuntuforums.org/showthread.php?t=1093272")

So I added 
acquire::http::proxy "http://username:password@wwwcache.myuniversity.fr:8080";
at /etc/apt/apt.conf

Now I'm getting this error when trying sudo update:

"Failed to fetch [http://archive.ubuntu](http://archive.ubuntu).......  Something wicked happened resolving 'wwwcache.myuniversity.fr:8080' (-5 - No address assciated with hostname)"[/I]

---

### Post by cortman on 2012-02-03
Odd. Looks like something's wrong with address. Did you try it in this format-

```
acquire::http::proxy "http://username:yourpass@proxyaddress:theport"
```

no "cache" after www.

What if you'd put in what the tech did? 

```
http:\\*institute domain name*\proxy.pac
```

Keep me posted. Good luck!

---

### Post by bonedriven on 2012-02-03
> **cortman said:**
> Odd. Looks like something's wrong with address. Did you try it in this format-

```
acquire::http::proxy "http://username:yourpass@proxyaddress:theport"
```

no "cache" after www.

What if you'd put in what the tech did? 

```
http:\\*institute domain name*\proxy.pac
```

Keep me posted. Good luck!

Hi Cortman,

I actually had a little progress, but still not connecting.

I found the correct address as ```
proxy.universityname.fr:8080
```
Then I got another error "cannot connect" (Other addresses would always be a "can't resolve" error.

Then I changed the port from 8080 to 8000, still a "cannot connect" error.

Then I changed the port to 80. Now it's another new error "Ign and Err 404 not found".

Don't know what to do now...

---

### Post by cortman on 2012-02-03
Does the proxy require a username/password? If so you might double check that that's right.
Try port 81 yet, if you haven't already.
Sounds like a little progress, anyway.

---

### Post by bonedriven on 2012-02-03
> **cortman said:**
> Does the proxy require a username/password? If so you might double check that that's right.
Try port 81 yet, if you haven't already.
Sounds like a little progress, anyway.

I am using the computer of my university. My browser works without problem with that proxy.pac. I didn't enter my username password nowhere.

Result:

1 proxy.univname.fr:80    404 error
2 univname.fr:80              Ign........Waiting for headers
3 proxy.univname.fr:81    unable to connect to proxy.univname.fr:81
4 univname.fr:81              
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

Holy...What does all this mean...?

---

### Post by bonedriven on 2012-02-03
OMG I DID IT! :D

I was so stupid. I have actually read the proxy.pac file many times but didn't realize there was the address I need! There's that address "proxy.univname.fr:3128"

I changed it to that address, now it's downloading!!!"
Thanks Cortman for the help too! I wouldn't have the patience to even try till now without you! :D

---

### Post by cortman on 2012-02-03
Wait! On port 80 (univname.fr:80 Ign........Waiting for headers) did you let it run for a while? Ign isn't necessarily an error message. That one looks like it might work.

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

This is a simple error- apparently you have an apt process running in the background, or else some other package manager. Whatever package manager is currently running "locks" the list of repositories so that no other package manager can run. Close out of all terminals, software center, synaptic, etc., and try it again.

---

### Post by cortman on 2012-02-03
> **bonedriven said:**
> OMG I DID IT! :D

I was so stupid. I have actually read the proxy.pac file many times but didn't realize there was the address I need! There's that address "proxy.univname.fr:3128"

I changed it to that address, now it's downloading!!!"
Thanks Cortman for the help too! I wouldn't have the patience to even try till now without you! :D

In that case you can ignore my previous post. Fantastic! I'm glad it's finally working for you- great feeling, isn't it?

I'm glad to be of any help I can. Have fun with Ubuntu, and if you have any more questions feel free to post.

Also mark this thread as [SOLVED] if you would. Thanks, and best wishes!

---

### Post by bonedriven on 2012-02-03
> **cortman said:**
> In that case you can ignore my previous post. Fantastic! I'm glad it's finally working for you- great feeling, isn't it?

I'm glad to be of any help I can. Have fun with Ubuntu, and if you have any more questions feel free to post.

Also mark this thread as [SOLVED] if you would. Thanks, and best wishes!

Yeah...I've struggled more than 5 hours for this...

BTW, the "username password" part IS redundant. I cut that part but still can update!

Best wish to you too!

---

