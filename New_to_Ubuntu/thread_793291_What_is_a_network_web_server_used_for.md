---
title: "What is a network web server used for?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Overwhelmed on 2008-05-13
Disclaimer: Dumb newbie question to follow...

I am attempting to set up a file server where I work. I am completely new to Linux, and although I have some experience with networking and working with Windows systems, I have feeling a bit overwhelmed with trying to learn both Ubuntu and more advanced networking tasks.

So please be understanding with my many stupid questions that will be incoming. :)


While Googling to learn how to set up an office file server (with Ubuntu Server 8.04), I have come across a lot of articles recommending I also install a web server (Apache). I think I understand what a web server is (to host web pages for other computers to view), but what I do not understand is what value that has in an office network.

If my file server is in an office network with a static IP address from the router (i.e. 192.168.0.100) only computers in the network can link to it; what benefit is an Apache web server in this situation?

If it is useful or simply nice to have for any reason, I will be quite happy to learn it and set it up. I am just not sure what value it would have.

I appreciate any attempts to educate this networking dummy. :)

---

### Post by tamoneya on 2008-05-13
apache is an http server.  What this would do is it would allow someone in your office to type: "192.168.0.100" into firefox and then be able to browse select directories and files on the server.  You should install it if you find this feature useful.  Personally I recommend that you install an ssh/scp server and it can be done as follows.```
sudo apt-get install ssh
```Then people in the office can download winSCP and use it to browse the entire filesever as well as upload files into user directories.  I recommend this because it is first of all encrypted but also allows for uploading and downloading unlike the apache http server.

---

### Post by mlentink on 2008-05-13
> **Overwhelmed said:**
> If it is useful or simply nice to have for any reason, I will be quite happy to learn it and set it up. I am just not sure what value it would have.



Well... it won't be in your way...
But if you google around for 'intranet', you might begin to understand how it could be useful. Many groupware packages depend on the availability of a http-server as well.

I have very good experiences with [HowToForge]("http://www.howtoforge.com/"), by the way...

---

### Post by Overwhelmed on 2008-05-13
> **tamoneya said:**
> apache is an http server.  What this would do is it would allow someone in your office to type: "192.168.0.100" into firefox and then be able to browse select directories and files on the server.  You should install it if you find this feature useful.  Personally I recommend that you install an ssh/scp server and it can be done as follows.```
sudo apt-get install ssh
```Then people in the office can download winSCP and use it to browse the entire filesever as well as upload files into user directories.  I recommend this because it is first of all encrypted but also allows for uploading and downloading unlike the apache http server.

Wow! Thank you very much; I think I get it now! :)

Basically, it is not for use on the external internet, it is used within the network as kind of a GUI for the file server, right?

I installed "lamp" and ssh. I typed in the IP of the server and got "It Works!", so I guess that is a good thing :cool:. Nothing there yet to see obviously.


As far as the winSCP, do I install that on the server as well, or is it for the other computers that link to it?

Thanks again!):P

---

### Post by drubin on 2008-05-13
> **tamoneya said:**
> apache is an http server.  Personally I recommend that you install an ssh/scp server and it can be done as follows.Then people in the office can download winSCP and use it to browse the entire filesever as well as upload files into user directories.  I recommend this because it is first of all encrypted but also allows for uploading and downloading unlike the apache http server.

Winscp is VERY slow! It would have to encrypt the data first, and seems as though the data is not leaving the "interanet" is this really necessary?

I would rather recommend installing a basic ftp server, used proftp before  then you could use any ftp client.  Would be alot faster.

Any one have other options on this?

---

### Post by drubin on 2008-05-13
Sorry forgot to add.

If this is a network file sharing server. (And that is all it is) take a look at samba rather.
```
sudo apt-get install samba
``` 

This would allow windows users to access shares on the server by just typing in the  computers name. ie in windows run prompt
```
//officeserver/sharename
```

---

### Post by upthelum on 2008-05-13
> **rubinboy said:**
> Sorry forgot to add.

If this is a network file sharing server. (And that is all it is) take a look at samba rather.
```
sudo apt-get install samba
``` 

This would allow windows users to access shares on the server by just typing in the  computers name. ie in windows run prompt
```
//officeserver/sharename
```

Recommend Samba

---

### Post by drubin on 2008-05-13
> **upthelum said:**
> Recommend Samba

Sorry but never/still cant see any posts by you?

---

### Post by tamoneya on 2008-05-13
> **Overwhelmed said:**
> Wow! Thank you very much; I think I get it now! :)

Basically, it is not for use on the external internet, it is used within the network as kind of a GUI for the file server, right?

I installed "lamp" and ssh. I typed in the IP of the server and got "It Works!", so I guess that is a good thing :cool:. Nothing there yet to see obviously.


As far as the winSCP, do I install that on the server as well, or is it for the other computers that link to it?

Thanks again!):P

The "it works file" is /var/www/index.html.  If you delete that file apache will list all the files and directories in /var/www/
```
sudo rm /var/www/index.html
```

---

### Post by Overwhelmed on 2008-05-13
> **rubinboy said:**
> Sorry forgot to add.

If this is a network file sharing server. (And that is all it is) take a look at samba rather.
```
sudo apt-get install samba
``` 

This would allow windows users to access shares on the server by just typing in the  computers name. ie in windows run prompt
```
//officeserver/sharename
```
Thank you for the help. I plan to use Samba.

This shows how clueless I am; this is a network file sharing computer and I already installed Samba, but I did not realize that winSCP was the same thing. :oops:

I am still reading and figuring out how to configure Samba and the network; expect a few more dumb questions over the next few days.

---

### Post by Overwhelmed on 2008-05-13
> **tamoneya said:**
> The "it works file" is /var/www/index.html.  If you delete that file apache will list all the files and directories in /var/www/
```
sudo rm /var/www/index.html
```

Cool, that is good info!

Thanks again.

---

### Post by drubin on 2008-05-14
> **Overwhelmed said:**
> 
This shows how clueless I am; this is a network file sharing computer and I already installed Samba, but I did not realize that winSCP was the same thing. :oops:
WinSCP is not the same thing as samba.

Samba: Is a network file sharing protocol so you can access files/folders via the OS(window's) my network places...  and such

WinSCP: is a client side application that allows one to connect to a secure(encrypted) FTP(file transfer protocol --I think) server. This could be accessed via any where if you knew the ip address.

> **Overwhelmed said:**
> 
I am still reading and figuring out how to configure Samba and the network; expect a few more dumb questions over the next few days.

That is what we are here for! :P

---

### Post by fredEbay on 2008-05-14
>  I am still reading and figuring out how to configure Samba and the network; expect a few more dumb questions over the next few days.

Overwhelmed - 

You have received good useful suggestions and there is great potential in the implementations, especially Samba in your case.

Insofar as your inquiry regarding "network 'web' server" is concerned - (and this isn't a perfect explanation or example in and of itself)

In an intranet environment you can develop a 'user friendly' interface (links or accessibility to) files stored on the file server, to other services and resources on the local network such as interoffice only and-or even internet mail, to other references and resources both internal and external, such as printers, scanners, cameras, etc. You would essentially develop a 'mini-web', an "office-wide-web" within your organization.

This in itself could promote efficiency making it easier to find, use, maintain and provide access to such resources within your office. Instead of having to always having to entirely use console/keyboard entry to gain access to files, printers, machines, etc, workers/users can point and click their way to these. 

(would you rather click once on an image or type the entire path to a given file, making sure you don't misspell something or can even remember where it is located? What about the other folks in the office trying to do the same thing day in and day out?)

A 'web' (http) server is not limited to providing pretty pictures, links, and so forth to the entire world even though this is what most people envision whenever the terms is mentioned.

Properly designed, configured, and secured and maintained, the http server can be a very important part of the entire office/company infrastructure.

There is basically no difference between 'web' serving on the internet and 'web' serving in the office - it is all in the coding/location of the resources your are providing the graphical/common user interface for.

---

### Post by hyper_ch on 2008-05-14
> **rubinboy said:**
> Winscp is VERY slow! It would have to encrypt the data first, and seems as though the data is not leaving the "interanet" is this really necessary?

Encryption is normally quicker than average network speeds :)

---

### Post by drubin on 2008-05-14
> Encryption is normally quicker than average network speeds 

Could you please explain why copying via winscp is much slowing then basic ftp? 

Thanks

---

### Post by hyper_ch on 2008-05-14
may depend on your cpu ;)

---

