---
title: "Can't download some programs"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by Tarek_Aboabdallah on 2014-05-17
Hi all 
I'm new at Ubuntu and I really like it after years of using Windows,
the story that I can't download some programs like Skype or vlc or any other Ubuntu program "I only can download google chrome and Smplayer "

when I enter to Software Center and chose a program to install the system show me a letter "I will put it with the post"
And even if I chose repair or OK it will tell me to check the internet connection "I'm using it now so it's not the problem"

so any one can help me?[ATTACH=CONFIG]253253[/ATTACH]

---

### Post by ibjsb4 on 2014-05-18
Please post the output of

```
sudo apt-get update
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

using code tags

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

And welcome to the forums :)

---

### Post by Tarek_Aboabdallah on 2014-05-21
> **ibjsb4 said:**
> Please post the output of

```
sudo apt-get update
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

using code tags

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

And welcome to the forums :)




thanks 

that's what happen

tarek@tarek-Latitude-E6410:~$ sudo apt-get update
[sudo] password for tarek: 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]                     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [58.5 kB]                       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources [1,064 kB]                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:6 [http://dl.google.com](http://dl.google.com) stable InRelease [1,540 B]                          
76% [6 InRelease gpgv 1,540 B] [3 Sources 799 kB/1,064 kB 75%] [Waiting for heaSplitting up /var/lib/apt/lists/partial/dl.google.com_linux_chrome_deb_dists_stabIgn [http://dl.google.com](http://dl.google.com) stable InRelease                                      
E: GPG error: [http://dl.google.com](http://dl.google.com) stable InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)

---

### Post by Harsh_Parikh on 2014-05-21
You should add repository from software center>edit>software sources>other software>add vlc repository.......

---

### Post by veddox on 2014-05-21
Neither VLC nor Skype installation should require adding extra repositories. 

The image you attached indicates that you have some keys missing. I had a similar problem under 12.04, where I solved it with a little trick:

In the Software Center, go to Edit->Software Sources. In the window that opens you will see the option "Download from:". Click on the drop-down menu, and choose any other server, it doesn't matter which one. (You will need to authenticate this action.) Once it's been changed, change it back again to what it was before.

Switching download servers causes the updater to download the relevant server's public keys, which it needs to check packages for authenticity. Thus, when you switch back to your original server, you have a complete set of keys again. Hopefully you should be able to download and install programs normally now.

NOTE: this is not the "official" way of updating keys. However, the proper method involves quite a bit of commandline juggling, so this method is quite a bit easier :-)

---

### Post by ibjsb4 on 2014-05-21
> Switching download servers causes the updater to download the relevant server's public keys, which it needs to check packages for authenticity. Thus, when you switch back to your original server, you have a complete set of keys again. Hopefully you should be able to download and install programs normally now.
Thats a neat little trick :) But if you click on that dl.google.com link you will see that its going to the chrome download page.  Not a proper link and should be removed.

Then update again and you should get a 'gpg error bagsig'.  You can now try veddox's method of repair or some command line juggling :)
```
sudo apt-get clean
sudo mv /var/lib/apt/lists /var/lib/apt/lists.broke
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update

```

---

### Post by Tarek_Aboabdallah on 2014-05-21
Well I try to switch the server but nothing change :(
the story that I live in Syria and we have no server so I chose the main server

---

### Post by Tarek_Aboabdallah on 2014-05-21
> **ibjsb4 said:**
> Thats a neat little trick :) But if you click on that dl.google.com link you will see that its going to the chrome download page.  Not a proper link and should be removed.

Then update again and you should get a 'gpg error bagsig'.  You can now try veddox's method of repair or some command line juggling :)
```
sudo apt-get clean
sudo mv /var/lib/apt/lists /var/lib/apt/lists.broke
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update

```


well when I started to enter this code 
this code 
sudo mv /var/lib/apt/lists
 give me this result 
mv: missing destination file operand after ‘/var/lib/apt/lists’
Try 'mv --help' for more information.

---

### Post by Tarek_Aboabdallah on 2014-05-21
> **Harsh_Parikh said:**
> You should add repository from software center>edit>software sources>other software>add vlc repository.......


form where I can get the vlc or other programmes repository ??

---

### Post by ibjsb4 on 2014-05-21
> **Tarek_Aboabdallah said:**
> well when I started to enter this code 
this code 
sudo mv /var/lib/apt/lists
 give me this result 
mv: missing destination file operand after &#8216;/var/lib/apt/lists&#8217;
Try 'mv --help' for more information.
Did you copy and paste (one line at a time)?

---

### Post by Tarek_Aboabdallah on 2014-05-21
> **ibjsb4 said:**
> Did you copy and paste (one line at a time)?

yes sure

---

### Post by ibjsb4 on 2014-05-21
Thats what I get too
```
sudo mv /var/lib/apt/lists
mv: missing destination file operand after &#8216;/var/lib/apt/lists&#8217;
Try 'mv --help' for more information.
```
When I enter half the command.  The full command is ..
```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.broke
```

---

### Post by Vladlenin5000 on 2014-05-21
Half commands won't work, ever... Why are insisting in NOT following the instructions?

```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.broke
```
cannot be dismembered

---

### Post by Harsh_Parikh on 2014-05-22
@Tarek..

You should refer [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu),if you download and install it from software sources,you don't need to do this.....and while downloading any software for ubuntu,sites give repository itself,you don't need to find them...

---

### Post by Tarek_Aboabdallah on 2014-05-22
Really thanks guys for helping me with the problem :)
I find a solution 
I install the same version on another Laptop and see the different in the setting list and fix it 
:)
thanks all

---

