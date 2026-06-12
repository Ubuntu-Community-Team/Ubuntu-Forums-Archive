---
title: "lampp cant find my php files"
date: 2010-08-17
forum: Programming Talk
---

### Post by thorbs on 2010-08-17
I have also posted this in absolute beginner twice, but as I did not get any answer I also try posting it here. Thanks for your time. 


Lampp cant find my php files

I am new to php programming and have installed lampp on ubuntu in order to practice. I am fairly newbee, so maybe the following problem is just some simple thing I dont get. 

I have recently installed lampp. It was my second try. The first time I ended up having a severe crash that was  hooked into a problem with updating the mysql, which crashed all attempt at updating ubuntu. Before this I created my sandbox files where I have lots of my different php files. 
I solved the problems with lampp by finding a way to uninstall  from the end of the thread here [http://ubuntuforums.org/showthread.p...install&page=3](http://ubuntuforums.org/showthread.p...install&page=3) and reinstall using this method [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies). 

Now I have Lampp well installed. I have tested it according to the instructions with localhost and  creating the tetsphp.php  file that contains info php. this file, and it test well. It is able to find localhost and the testphp.php file, that has a info in it. But it cant find anything else, that is except for a helloworld file in my sandbox file, that is not shown in the directory?!? On the other hand it can not find the helloworld file that is actually there. 

I am not able to save any new files and then make lampp recognise it. At the same time I am not able to find any of all my old phpfiles.  

What is going on, can anybody help?

---

### Post by sanderd17 on 2010-08-17
The only thing you need to do is fire up synaptic, search for php and install the newest version.

Than, go to /var/www and make it writable as normal user. In code:
```

cd /var
sudo chown [USERNAME] www

```

Afterwards, all php files have to come in the www directory and you can execute them by going in your browser to [http://localhost]("http://localhost")

Good luck

PS. no need to double post: [http://ubuntuforums.org/showthread.php?p=9730892#post9730892]("http://ubuntuforums.org/showthread.php?p=9730892#post9730892")

---

### Post by thorbs on 2010-08-18
I have allready got the newest php, and mysql, and it is being updated automatically. I have also made the var/www writable, I am able to make files and save files. 

I am using the [http://localhost](http://localhost). My problem is that for some reason lampp is not able to find the files that I have saved in var/www.


thanks.

---

### Post by thorbs on 2010-08-18
Ok, really weird I solved it. For some reason there was an extra www directory in my rootfolder. I was writing to the wrong directory. Must have have something to do with me installing de-stalling and installing again.

thanks for your time.

t.

---

