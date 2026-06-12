---
title: "File sharing solution.  Owncloud, Samaba, other solutions?"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-11-02
I'm looking into a simply file server solution for my server.  Something my family can use from their assorted devices.  Something responsibly secure.

I'm in the learning phase of Ubuntu/Linux hence the question.

Can this community offer some thoughts on solutions that might allow for the sharing of content within my home network?  I'm adverse to storing this content in a public cloud solution.

Owncloud looks interesting, but every time I search for solutions along these lines Samba seems to dominate google searches.

---

### Post by TheFu on 2015-11-02
TL;DR - use **sftp** with ssh-keys for authentication. DO NOT USE PASSWORDS. Every networked OS has a nice sftp client.

Longer answer.

ssh is amazing. [http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](http://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh) explains.
For non-technical users, the subtle differences between ssh and a VPN are lost and the  connections for  ssh/scp/sftp can be complex. Using an OpenVPN-based solution that sends **all** traffic through a secure connection is easiest. With openvpn, any other protocol/service can be use like RDP, VNC, CIFS, HTTP, SMTP without concern whether the client/server connection is encrypted  for self-hosted stuff  like  owncloud. Without a VPN, each of those protocols is either completely non-secure or the security is terribly inadequate. **Owncloud should never be used without a fullVPN, like openvpn.**   HTTPS has been broken for years. Don't trust it without the liability shifted to someone else.

Hope that helps.  If you just use sftp with keys, that is by-far the easiest to setup for remote file access from anywhere in the world.

---

### Post by HereInOz on 2015-11-02
If you want synchronised file sharing across multiple devices, then ownCloud will do very nicely.  It is essentially a personal DropBox.  I have used it for 12 months now on a basic piece of hardware and it has been pretty solid. 

It is different from Samba in that with Samba, the files exist in only one place, and all devices access those files across the network, use those files and then they are saved back to the server.  If someone takes a local copy of a file, and works with it, that file becomes a "version orphan", different from the original, until that file is copied to the server, overwriting the server version.  So, files copied from the server to a local machine are not going to update each other.  For version stability, all files need to be opened from the server, and then saved to the server.  If the computer is out of the LAN, at a remote location, things get a little difficult.

OwnCloud provides fully synced copies of files across all connected computers, automatically, maintaining a local synced copy on the computer.  So, if you open a file in your ownCloud folder on your computer, edit it, and save it, it syncs to the server and thence to all other connected computers, even if those computers are Internet connected, not only LAN connected.  As I said, it is a private DropBox type of thing, but because you can have the computers LAN connected, syncing large amounts of data is easier and quicker than it is with a cloud service like DropBox.

Personally, from the point of view of home networking, with users who are not all that conversant with file servers and the like, I would go with ownCloud.

---

### Post by eddiefiggie on 2015-11-03
I'm going to go Owncloud.  Thanks for the guidance everyone.

---

### Post by TheFu on 2015-11-03
Owncloud is good on a LAN when you desire copies of files to be made. Not a bad choice. It is definitely to most mature in this space. Seafile is another option for people adverse to php risks.

If your files are audio/video or ebooks, then there are better choices for a LAN environment.

---

### Post by eddiefiggie on 2015-11-03
> **TheFu said:**
> Owncloud is good on a LAN when you desire copies of files to be made. Not a bad choice. It is definitely to most mature in this space. Seafile is another option for people adverse to php risks.

If your files are audio/video or ebooks, then there are better choices for a LAN environment.


The idea it was written in PHP did bother me.  Not that I fully understand its vulnerabilities, but I've read bad press about PHP in general with regards to security issues.

Seafile (C, Python)...  Now that sounds interesting.  I'll look into that one!

So many good options out there, I love it!

Most of my content are stills, and documents.

---

### Post by MartyBuntu on 2015-11-03
DropBox for ease of use and cross-platform compatibility.

---

### Post by eddiefiggie on 2015-11-03
> **MartyBuntu said:**
> DropBox for ease of use and cross-platform compatibility.

Trying to keep my content at home.

Side note, after reviewing Seafile further, the license agreemet seems to have a fee connected to it for more than 3 users.  =(  I had intended to connect 5 total people to it.

Owncloud is back in the running.

---

### Post by SeijiSensei on 2015-11-03
Claims about the "insecurity" of PHP are overwrought.  Most problems arise because the person writing the code doesn't think about security, not because the language is itself insecure. One reason is that PHP is easy enough to use that many people start off with it and have never thought about the issues of writing an application that will be exposed to a hostile world on the Internet.  I've been writing applications in PHP for about two decades, one of which was for a community health center and had to meet HIPAA requirements.  I've never had an application breached that I know of.  

Many large-scale web applications like WordPress and Joomla are written in PHP.  Yes, they have had many security updates over the years, but those arise largely because these applications support third-party add-ons and have to run on hosted web accounts.  Not all developers for these applications are security-conscious either.  That same health center had someone design their web site with Joomla, and it was eventually defaced because the developers left most of the web tree writable by the Apache server user.  Those are the kinds of problems that a little thought about security in advance would have fixed. (I had long since disengaged myself from this project because it was clear the marketing people would be in charge, and their only concern was whether the web site was attractive, not whether it was secure.)

---

### Post by mastablasta on 2015-11-04
> **eddiefiggie said:**
> 
Side note, after reviewing Seafile further, the license agreemet seems to have a fee connected to it for more than 3 users.  =(  I had intended to connect 5 total people to it.


that is not true. the license make that limit on the pro version, however community version is free. Pro version would be aimed at businesses so they charge per users. 


> **Deploy Seafile on Your Own Server**

              [TABLE="class: table table-striped"]
[TR]
[TH]Products[/TH]
[TH]Price[/TH]
[TH="width: 50%"]Note[/TH]
[/TR]
[TR]
[TD]**[COLOR=#ff0000]Community Edition[/COLOR]**
[/TD]
[TD]**[COLOR=#ff0000]Free & Open Source[/COLOR]**
[/TD]
[TD]Go to the downloads page[/TD]
[/TR]
[TR]
[TD]Professional Edition and Support[/TD]
[TD]See the section below[/TD]
[TD]The pro edition runs on Linux platform only[/TD]
[/TR]
[/TABLE]
              **Pricing of Pro Edition license (yearly subscription)**

                               [TABLE="class: table table-striped"]
[TR]
[TH]Number of users[/TH]
[TH]Price /Year[/TH]
[TH]Price for Educational /Year[/TH]
[/TR]
[TR]
[TD]3 users[/TD]
[TD]Free[/TD]
[TD]Free[/TD]
[/TR]
[TR]
[TD]9 users[/TD]
[TD]90,00 &#8364;[/TD]
[TD]90,00 &#8364;[/TD]
[/TR]
[TR]
[TD]From 10 to 249[/TD]
[TD]44,00 &#8364; /User[/TD]
[TD]22,00 &#8364; /User[/TD]
[/TR]
[/TABLE]
 ...

---

### Post by eddiefiggie on 2015-11-04
Ah!  Thanks for clearing that up.

---

### Post by Geoffrey_Arndt on 2015-11-04
Before "dropping" your file(s) or directories into the Dropbox directory/folder at your user /home . . . . just encrypt it.   Dropbox will not have your password, and unless I'm mistaken, the use of 7z (7zip) AES 256 encryption should be plenty secure from both Dropbox or hackers who may access their servers.    

If really paranoid about security, the user can also do kgpg using twofish 2048 or 4096  . . doubtful if any backdoors in that.

So, given above, besides the modest cost . . . what's the down side?   Dropbox requires virtually no time to setup or manage.

---

