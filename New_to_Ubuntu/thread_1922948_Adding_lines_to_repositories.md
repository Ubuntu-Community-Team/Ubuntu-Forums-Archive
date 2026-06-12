---
title: "Adding lines to repositories"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by Robbo35 on 2012-02-09
Hi,  I'm trying to get Spotify for Linux downloaded - running on Ubuntu 11.10.  

The instructions on their website are :

**Debian**

 # 1. Add this line to your list of repositories by #    editing your /etc/apt/sources.list deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free  #
 2. If you want to verify the downloaded packages, #    you will need to add our public key sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E  # 
3. Run apt-get update sudo apt-get update  #
 4. Install spotify! sudo apt-get install spotify-client-qt

Unfortunately I don't know what my repository is!  

Can someone translate this into very simple, very slow person language please?

Thank you

---

### Post by divague on 2012-02-09
Hi, lets see if I can clarify this to you. First you have to open a terminal and run this command
```
sudo gedit /etc/apt/sources.list
```

then you have to add this line to the file, I usually add new repos at the bottom.
```
deb http://repository.spotify.com stable non-free
```

save the file and close the text editor. Now you have to run this command to add the repo key.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
```

Now run this
```
sudo apt-get update
```

And to install the program run this
```
sudo apt-get install spotify-client-qt
```

---

### Post by Lateralis on 2012-02-09
Ah, another Spotify user!  Huzzah!  

divague has covered what you need to do.  I would, however, suggest that you type

```

**gksudo** gedit /etc/apt/sources.list

```

instead of 

```

sudo gedit /etc/apt/sources.list

```

You won't break your system by using *sudo gedit*, but best practice is to use *gksudo*


To explain a little bit more though, software in Ubuntu can be downloaded from so-called "repositories" which are essentially where programs are kept.  When you want to install a program using either the command line through apt-get, or through the Ubuntu software centre, Ubuntu looks at the file /etc/apt/sources.list to know which repositories to look in for the programs that you want.  There are a various repositories, each repository distributing different programs.  Spotify has its own repository for the Spotify Linux client, but this repository isn't listed in /etc/apt/sources.list by default; you have to add it manually otherwise Ubuntu will have no clue about the program you want.  That is what the first line in the instructions was telling you to do. =)  Once the repository is added to /etc/apt/sources.list, you can set about installing Spotify!  


Hope this helps! =)

---

### Post by Robbo35 on 2012-02-10
Thank you both of you, that makes more sense now.  I shall try when I'm home tonight and let you know how I get on!  Many thanks.

---

### Post by The Grate One on 2012-02-11
Thanks for the help and explanation!! It helped me out tremendously and my Spotify is working:guitar:

---

### Post by Robbo35 on 2012-02-19
Thanks for all the help!  Spotify now working a treat.  Cheers

---

### Post by jmarkybb on 2012-03-02
Hiya,


I'm a complete noob too, I have gotten this far-

Code:

sudo gedit /etc/apt/sources.list

then you have to add this line to the file, I usually add new repos at the bottom.
Code:

deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

save the file and close the text editor.

but then I come across a brick wall

I cant figure this part out -

Now you have to run this command to add the repo key.
Code:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

Now run this
Code:

sudo apt-get update

And to install the program run this
Code:

sudo apt-get install spotify-client-qt

Can anybody clarify, step by step sorry to be a bind.

---

### Post by cmcanulty on 2012-03-02
the sudo add key line adds the key to ubuntu then the update line lets ubuntu see the new repository and key then the last command installs the program

---

### Post by jmarkybb on 2012-03-02
Where do I copy and paste these lines though?

Now you have to run this command to add the repo key.
Code:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

Now run this
Code:

sudo apt-get update

And to install the program run this
Code:

sudo apt-get install spotify-client-qt

---

### Post by audiomick on 2012-03-02
That all happens in the terminal.

---

### Post by Miljet on 2012-03-02
Go back and reread the instructions carefully. I think you missed the part about saving the file and closing the text editor. That will take you back to the terminal where you can enter the next code.

---

### Post by bodhi.zazen on 2012-03-02
I suggest you read this

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Repositories can be added graphically as well, from the software center

[img]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-AddApt2.png[/img]

---

### Post by jmarkybb on 2012-03-03
I have got this far, now I am stuck.

Clicking the icons does not do anything.

---

### Post by jmarkybb on 2012-03-04
I'm getting there with your help guys, but not quite, I've read all the documentation and that is as far as I can get.

---

### Post by howefield on 2012-03-04
Close the software centre, open a terminal and type

```
sudo apt-get install spotify-client-qt
```

What does it want to do ?

---

### Post by jmarkybb on 2012-03-04
That icon comes up in top left corner.

Then I go to Software Centre...

---

### Post by yetiman64 on 2012-03-04
> **jmarkybb said:**
> That icon comes up in top left corner.
Open Dash and search for "Terminal" (without the quotes). 

Click the Terminal icon that shows when you do. 

Paste your commands into the terminal that opens. The run command dialog doesn't always work with all terminal commands.

---

### Post by howefield on 2012-03-04
No, I mean a terminal.. press Ctrl + Alt + T to open a terminal and type into that.

See screenshot eg..

---

### Post by jmarkybb on 2012-03-04
Ahhhh!

That's never happened before...

---

### Post by jmarkybb on 2012-03-04
We have sussed it!!!!


Thank you very much guys:D:D:D:D:D


I could kiss ya!!!


Is there an app called Evernote for Ubuntu?

---

### Post by howefield on 2012-03-04
> **jmarkybb said:**
> I could kiss ya!!!

Glad you're sorted but please, you must resist ;-)

Just one small note, when using the terminal and you have a choice like Y/n - the upper case is the default, meaning you don't need to type the Y, you may simply press enter to select it.

> Is there an app called Evernote for Ubuntu?

Never used it myself, but you might have a look at Nevernote.

[http://www.omgubuntu.co.uk/2010/10/nevernote-gives-ubuntu-users-access-to-evernote/](http://www.omgubuntu.co.uk/2010/10/nevernote-gives-ubuntu-users-access-to-evernote/)
[http://nevernote.sourceforge.net/](http://nevernote.sourceforge.net/)

---

### Post by jmarkybb on 2012-03-04
> **howefield said:**
> Glad you're sorted but please, you must resist ;-)

Just one small note, when using the terminal and you have a choice like Y/n - the upper case is the default, meaning you don't need to type the Y, you may simply press enter to select it.



Never used it myself, but you might have a look at Nevernote.

[http://www.omgubuntu.co.uk/2010/10/nevernote-gives-ubuntu-users-access-to-evernote/](http://www.omgubuntu.co.uk/2010/10/nevernote-gives-ubuntu-users-access-to-evernote/)
[http://nevernote.sourceforge.net/](http://nevernote.sourceforge.net/)

Ok, I wont kiss you, I would buy you a beer instead, thanks for the help and link for NeverNote, its appreciated. Your a :KS

---

### Post by jmarkybb on 2012-03-04
Is there a list of apps that I can browse that are 3rd party?

---

### Post by howefield on 2012-03-04
Hmm.. can you be more specific ?

Also, if you are veering away from the topic of "Adding lines to repositories" might be best to start a new thread in the appropriate location. :)

---

### Post by bodhi.zazen on 2012-03-04
> **jmarkybb said:**
> Is there a list of apps that I can browse that are 3rd party?

You have hijacked another thread that has been marked as solved and are drifting further and further from the original topic. You are going to get better results if you start a new thread.

---

