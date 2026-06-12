---
title: "HOW TO Make A Public gnump3d Server"
date: 2006-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by SDREnate on 2006-07-12
Note: I'm writing this HowTo because when I first set up my streaming media server, I couldn't find any resources that gave a good explaination of how to get my server accessible via the internet. This is what worked for me. A lot of this information can be found at [www.ubuntuguide.org](www.ubuntuguide.org), I basically elaborated on the whole process.


1. I started out by doing a server intall of Breezy. Next, I added extra repositories as described   [here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

2. First, install Apache2 HTTP server
```
sudo apt-get install apache2
```

3. Then, install gnump3d
```
sudo apt-get install gnump3d
```

4. The default port that is used by gnump3d is 8888. If you want to change this, refer to [these](http://ubuntuguide.org/wiki/Dapper#How_to_change_the_default_port_number_for_GNUMP3d")instructions.
You should now be able to view your gnump3d server on your LAN by typing ```
http://server'slocalIP:8888
```

If you just want to access your server only through you LAN, you don't have to do any more configuration. However, if you want to access it from any location through the internet, you have to do a little bit more work, which  I'll explain now.

5. First of all, you need to forward port 8888, or whatever port you changed gnump3's default port to, to the local IP of your server in your router's configuration. How you do this depends on your router make and model, so refer to your router's instruction manual if you're unsure on how to do this.

6. After you do this, you need your public IP address, because you cannot route your local IP from the internet. An easy way to find out your router's public IP is to visit a site like [ipadress.com]("http://www.ipaddress.com")

7. Once you know your public IP, it's time to edit your gnump3d.conf file.
First, backup your original file: 
```
sudo cp /etc/gnump3d/gnump3d.conf /etc/gnump3d/gnump3d_backup.conf
```
8. Then edit the file:
```
sudo nano /etc/gnump3d/gnump3d.conf
```
Find the line that reads:
```
# hostname = mp3d.foo.org
```
Uncomment it by removing the '#' then replace 'mp3d.foo.org' with your public IP
Example: ```
hostname = xx.xxx.xx.xxx
```
Then, save the edited file.

9. Now, restart gnump3d by typing: ```
sudo /etc/init.d/gnump3d restart
```

10. Gnump3d should know by accessible via the internet by typing [http://publicIP:8888](http://publicIP:8888)

11. Now, you'll probably want to add some files to gnump3d. The default directory is /var/music. If you want to change it, refer to [this guide]("http://ubuntuguide.org/wiki/Dapper#How_to_change_the_default_directory_containing_multimedia_files_for_GNUMP3d")
There are many different ways to copy files into your server from another Ubuntu machine, but I do it by using openssh. On the Ubuntu box that you want to copy the files from, open a terminal and type: ```
sudo apt-get install openssh
```
On your server, type: ```
sudo apt-get install openssh-server
```
Assuming that the path of a folder to copy is /home/username/music and the local IP of the remote Ubuntu computer is xxx.xxx.x.xxx, and the directory where the copied files will go is /var/music, go you your server and type: ```
cd /var/music
sudo su
scp -r username@xxx.xxx.x.xxx:/home/username/music .
```
Instructions on this can be found [here]("http://ubuntuguide.org/wiki/Dapper#How_to_copy_files.2Ffolders_from_local_machine_into_remote_Ubuntu_machine_.28scp.29")

You can also administer to your server using SSH, which can also be found at ubuntuguide.org.

That's about all there is. I hope this helps someone.

---

### Post by LucasLinard on 2006-07-15
nice topic!

---

### Post by gorilla_king on 2006-07-15
great job writing this, it actually worked 4 me. 
so it seems you know alot about setting up music servers, so maybe you can amswer this. 
I've got permission from many artists to play there music however i want. (podcast, radio, ect.) so i was wondering. Do u know of how or what software i would use to make an online radio station?

---

### Post by SDREnate on 2006-07-15
> **gorilla_king said:**
> great job writing this, it actually worked 4 me. 
so it seems you know alot about setting up music servers, so maybe you can amswer this. 
I've got permission from many artists to play there music however i want. (podcast, radio, ect.) so i was wondering. Do u know of how or what software i would use to make an online radio station?I've been wondering that myself actually. I'll let you know if I find anything.

---

### Post by simone.brunozzi on 2006-07-24
Did you find anything for online radio?

Cheers,

---

### Post by SDREnate on 2006-07-30
> **simone.brunozzi said:**
> Did you find anything for online radio?

Cheers,I found [this]("http://yolinux.com/TUTORIALS/LinuxTutorialAudioStreaming.html") . I wonder if there's anyone on here who's used it.

---

### Post by gjivan72 on 2006-07-31
Hey Great Tutorial. But is it possible to stream videos?

---

### Post by JHawk24821 on 2006-11-16
For those wanting to make their own internet radio station, jump over to [www.shoutcast.com]("www.shoutcast.com").  Everything you need is on the site, as well as links to servers already running SHOUTcast.  Check out a few stations to make sure it's what you want, then get it going!

---

### Post by Nano on 2006-11-20
Actually you don't have to install Apache in order to run gnump3d, it will automatically serve a web interface.
You won't even have to change the hostname if you use a dyndns service, which I strongly recommend since most of us don't have a fix ip.

---

### Post by gildotron3k on 2006-12-02
hi. i'm new to ubuntu and gnump3d. i'm looking for a way so that remote users would need to have a user account and password to access my music. i've found things on creating user accounts but nothing that applied to gnump3d itself. is there a way to do this or am i missing something ridiculously obvious?

thanks!

EDIT- i found the answer to my query. it seems it was something ridiculously obvious and staring me right in the face. thanks.

---

### Post by Jose Catre-Vandis on 2006-12-02
> **gildotron3k said:**
> hi. i'm new to ubuntu and gnump3d. i'm looking for a way so that remote users would need to have a user account and password to access my music. i've found things on creating user accounts but nothing that applied to gnump3d itself. is there a way to do this or am i missing something ridiculously obvious?

thanks!

The gnump3d.conf file provides you with opportunities to add users and passwords, to secure your gnump3d server. Read up on the gnump3d site, the man or in the conf file for syntax etc

---

### Post by gildotron3k on 2006-12-04
thanks. i had found the info already and have that aspect of it working perfectly. 

what i'm now looking for is a way for users to only access specific folders. for example i've made 2 user accounts. one for me which accesses my entire directory and one user account for guests which currently accesses the entire directory also but i'd like to set it up so that it only accesses a specific folder instead of the entire directory. 

i'm going to read up and see if i can find info on how to do that but if anyone knows a way to do it, or has done it themselves i'd greatly appreciate a link to the tutorial or a point in the right direction. thanks a lot!

p.s. songbird and gnump3d is an amazing combo. i love being able to have my entire music library accessible to me anywhere and playable thru a simple browser.

---

### Post by bodhi.zazen on 2006-12-05
Nice How-to

This thread has been added to the UDSF wiki.

[Public_gnump3d_Server](http://doc.gwos.org/index.php/Public_gnump3d_Server)

---

### Post by LosD on 2007-01-27
> **JHawk24821 said:**
> For those wanting to make their own internet radio station, jump over to [www.shoutcast.com]("www.shoutcast.com").  Everything you need is on the site, as well as links to servers already running SHOUTcast.  Check out a few stations to make sure it's what you want, then get it going!

Use [icecast]("http://icecast.org") instead, it's much better, open source (Shoutcast isn't, AFAIK), and supports much more formats (including video).

---

### Post by Roasted on 2007-02-18
Uh oh, bumping it to the top!

Question. I ran into a bit of a roadblock here. I did everything that was described in the howto guide perfectly. However, I ran into a small issue. Actually 2 of them. It says in 2 different sections to run your server to put in [http://publicip:8888](http://publicip:8888) and [http://localip:8888](http://localip:8888).

When I run local IP, I immediately get "Problem Loading Page." When I run public IP, it just sits there... loading... forever.... and times out. 

Now, I have a new router on the way. My old router I'm unable to change anything with. I can't change my username/password, I can't forward ports, I can't do anything. And it's been dropping our connection about once a day, requiring a power cycle to kickstart it. Perhaps it's my router blocking me? Maybe it's got port 8888 blocked. I don't know, and I'm not even going to attempt to figure it out because I'd rather stay online for this evening.

Are you folks betting that's what it is, or do I have another problem elsewhere? I have a strong feeling I just need to forward port 8888, but would that explain why when I try to run the public IP to access gnump3d server from the internet that it just hangs forever and eventually times out?

---

### Post by jkopp on 2007-02-19
I have had gnump3d running for sometime now without issue.  

I would like to use another form of authentication then what is provided within the gnump3d server.  I have other resources running on apache that I require basic authentication over SSL to access, and mutliple users frequent these resources.  I would like to make gnump3d available to only the users that can authenicate using the same basic authentication credentials that I already require for these other resources.  Has anyone tried to do this or know of way of doing so?  

To explain better I have gnump3d access available to anyone with the authentication credentials setup within gnump3d.conf.  This is available by going 'http://mydomain.com:8888'.  I have other resourses that are available by going to 'https://mydomain.com/private/my.other.resourses'.  Any requests to access anything within the private directory require basic authentication over SSL.  I would like to have gnump3d behind the private directory as well so that the same basic authentication credentials are required; something like 'https://mydomain.com/private/my.music:8888'.  

My initial thought was that this could be done using some mod-rewrite rule or by setting up a virtual host that ran gnump3d, but my attemps at this have failed.  

Any ideas???

---

### Post by otake-tux on 2007-05-09
I also have a problem.  

Everything works except the actual streaming of the songs.  Whenever streaming commences, the server freezes!

I've checked the config files and I did nothing wrong.  could it have something to do with the fact that it's on a wireless network?

---

### Post by gg234 on 2007-05-10
try[ this nice ]("http://www.ubuntugeek.com/streaming-media-server-in-ubuntu-gnulinux-using-gnump3d.html") gnump3d server guide with nice screenshots

---

### Post by sanjito on 2007-06-24
This was an excellent post. Other things i found on this subject, just made me mad. this worked first time thru. thanks alot

---

### Post by xfile087 on 2007-06-27
I wonder if anyone could help me?

I installed it and a weird thing happens. The server is showing every artist I have in my music folder however they all say there are 0 songs to play by that artist, except for albums i've added in the past week or so. Any ideas?

The funny thing is when I click random directory/selection it finds the actual songs but when I try to play it says the request file cannot be found?

**FIXED - something about folder access?**

---

### Post by pshown on 2008-12-30
I am a newbie to Ubuntu. I am trying to add the required repositories to get gnump3d. I found this post on adding repositories but I do not see the options outlined in adding  repositories to package manager. For instance;Under settings->Repositories I do not see a tab for Media to work with the instructions below. I may be not finding or seeing the obvious as I am so new to this. Can anyone help me along here?

# System -> Administration -> Synaptic Package Manager
# To enable the extra Universe and Multiverse repositories
   1. Settings -> Repositories
   2. In the Installation Media tab, click Add. There are three separate repositories; Dapper Drake, Security Updates and Updates. Select each repository and check Officially supported, Restricted copyright, Community maintained (Universe) and Non-free (Multiverse). Ensure you click OK between each repository to save your changes

---

### Post by fooman on 2008-12-30
that is an old guide.

when you open synaptic,  go to settings > repositories > ubuntu software tab

put a check next to the top 4 items (main - universe - restricted - multiverse)....close that box and you will see a message telling the repos have changed, close that box as well.

click "reload"

---

### Post by Jose Catre-Vandis on 2009-01-01
gnump3d is now sadly no longer in the ubuntu repos.

You can download a deb from here:
```
https://launchpad.net/ubuntu/intrepid/i386/gnump3d/3.0-2
```

---

