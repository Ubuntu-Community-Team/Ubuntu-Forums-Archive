---
title: "writeing a script that transfers files over FTP"
date: 2009-04-03
forum: Programming Talk
---

### Post by monkeyslayer56 on 2009-04-03
i didn't find anything when i was looking so first off im sry if this is a noob question and/or it ahs already been posted
ok what i want to do is have a script that when run will copy a local file to a remote location via FTP and i don't want it to prompt about overwriting so please help and is this even possable?

---

### Post by Arndt on 2009-04-03
> **monkeyslayer56 said:**
> i didn't find anything when i was looking so first off im sry if this is a noob question and/or it ahs already been posted
ok what i want to do is have a script that when run will copy a local file to a remote location via FTP and i don't want it to prompt about overwriting so please help and is this even possable?

I don't have a writable ftp repository to test on, but does perhaps the 'prompt' command turn off prompting in your case?

Does it work to first delete the file and then put it?

You can try to orchestrate the whole session, interactive and all, through the 'expect' program. With it, you can manage interactive programs programmatically.

---

### Post by monkeyslayer56 on 2009-04-03
what are you saying exactly? try doing it by hand then minipulate it in a script? and how would i start doing the script?

---

### Post by myrtle1908 on 2009-04-03
If you know Perl you could have a look at the Net::FTP module which makes things pretty easy.  For example (untested)

```
use strict;
use warnings;
use Net::FTP;

my $srv = "ftp.somewhere.com";
my $user = "username";
my $pass = "password";
my $put_dir = "/some/dir";
my $put_file = "myfile";


my $ftp = new Net::FTP($srv, Debug => 1) || die $ftp->message;
$ftp->login($user, $pass) || die $ftp->message;
$ftp->cwd($put_dir) || die $ftp->message;
$ftp->binary() || die $ftp->message; #may need this depending on type of file
$ftp->put($put_file) || die $ftp->message;
$ftp->quit();
```

---

### Post by ghostdog74 on 2009-04-03
an example
```

  ftp -n $SERVER <<EOF
  user $USERNAME $PASSWORD
  cd some_directory
  mput *.txt
  close
  bye
  EOF

```

---

### Post by Arndt on 2009-04-04
> **monkeyslayer56 said:**
> what are you saying exactly? try doing it by hand then minipulate it in a script? and how would i start doing the script?

If what ghostdog74 says works, I don't know what the problem was. But otherwise, things may get clearer if you show an example of a session, where you do it all by hand. Then we can put it in a script and try to solve the problem of avoiding a prompt when overwriting.

---

### Post by monkeyslayer56 on 2009-04-04
ok i try that when i get a chance cuz im not home right now and am on my laptop :( 
well exactly what i am trying to do is make a script that when run will copy a picture (doesn't matter format if one works better then anotehr for some reson when copying) to an ftp site so that when the website sees it  it see the new image and what i want it to be is after i get the script working have it run at boot so that it can upload an image saying im online sry if im not very clear but i struggle when it comes to explaining things :neutral:

---

### Post by myrtle1908 on 2009-04-04
> **monkeyslayer56 said:**
> ok i try that when i get a chance cuz im not home right now and am on my laptop :( 
well exactly what i am trying to do is make a script that when run will copy a picture (doesn't matter format if one works better then anotehr for some reson when copying) to an ftp site so that when the website sees it  it see the new image and what i want it to be is after i get the script working have it run at boot so that it can upload an image saying im online sry if im not very clear but i struggle when it comes to explaining things :neutral:

So you want to upload an image to a remote location via FTP when your machine "boots".  This image indicates that you are "online".  What happens when you go offline?  Would you need to replace that image to indicate that you are "offline"?  Doesn't sound like a very foolproof method to me.  Are you wanting to display this image on a website?

---

### Post by monkeyslayer56 on 2009-04-04
> **myrtle1908 said:**
> So you want to upload an image to a remote location via FTP when your machine "boots".  This image indicates that you are "online".  What happens when you go offline?  Would you need to replace that image to indicate that you are "offline"?  Doesn't sound like a very foolproof method to me.  Are you wanting to display this image on a website?
part of the reason i wanted to leave some of the deatils out on teh first post because people have a tendaty to do that im not worryed about shutting down yet i cna just get s simlilary sript adn manuel run it right before i get off and yes it will be on a website and thats y it needs to be able ot overwrite or the eqvilant of it becasue teh online and offline images will have the same name but right now i just want to know how to do a script that does this i can worry about  auto running later

---

### Post by myrtle1908 on 2009-04-05
> **monkeyslayer56 said:**
> right now i just want to know how to do a script that does this i can worry about  auto running later

In that case, the script that either I or ghostdog74 posted earlier will do just fine.

---

### Post by monkeyslayer56 on 2009-04-05
ok im home and tryed ghostdogs script becasue i don''t know any perl but i don't see were i tell it my local image is to upload can maybe u explan it a little bit and im sry for being such a n00b

---

### Post by ghostdog74 on 2009-04-05
to specify local directory, use lcd <path>
```

ftp -n << EOF
...
...
lcd /my/local/dir
put some_file.txt
...
...

```

---

### Post by monkeyslayer56 on 2009-04-05
i tryed
```
ftp -n $192.168.254.12 <<EOF
user $josh $******(blanked for my own safety)
cd www
lcd /home/josh/online.png
put online.png
close
bye
EOF
```
 and it doesn't work i know little about linux scripts (i was alright at batch files) so i  need everything explaned the ip of the host is corect and user and pass but i know i must be doing something wrong because its not working i know it might be obviose but i need help to learn the linux way of scripting

---

### Post by Arndt on 2009-04-05
> **monkeyslayer56 said:**
> i tryed
```
ftp -n $192.168.254.12 <<EOF
user $josh $******(blanked for my own safety)
cd www
lcd /home/josh/online.png
put online.png
close
bye
EOF
```
 and it doesn't work i know little about linux scripts (i was alright at batch files) so i  need everything explaned the ip of the host is corect and user and pass but i know i must be doing something wrong because its not working i know it might be obviose but i need help to learn the linux way of scripting

What are those dollar characters for? They seem out of place.

---

### Post by ghostdog74 on 2009-04-05
> **monkeyslayer56 said:**
> i tryed
```
ftp -n $192.168.254.12 <<EOF
...
lcd /home/josh/online.png
put online.png
...
EOF
```



```

lcd /home/josh/online.png

```
what is the meaning of lcd ?? and what is online.png? its a file, not a directory. get the hint?

---

### Post by monkeyslayer56 on 2009-04-05
ok sry i didn't pay attention to that but what exactly am i supposed to do ? i see now i didn't learn enough before i tried to get into this

---

