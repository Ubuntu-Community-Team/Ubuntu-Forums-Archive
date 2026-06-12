---
title: "E: Unable to locate package whatsapp-purple.."
date: 2015-06-28
forum: New to Ubuntu
---

### Post by simba4 on 2015-06-28
Ubuntu 64Bit.

For a week now, I am trying to migrate Pidgin-Whatsupp from Windows to Ubunto.  I already zipped all it's inner data from Windows (.purple folder) but I can't seem to install it on Ububtu.

The closest I get is by following _[[COLOR=#0000ff]this page instruction[/COLOR]]("https://davidgf.net/whatsapp/")_
I manage to go all the way up to the last instruction (number 4) whitch is '[COLOR=#800080]**sudo apt-get install whatsapp-purple**[/COLOR]'

It keep telling me: '**[COLOR=#800080]E: Unable to locate package whatsapp-purple[/COLOR]**'

(I suspect it relates to the 64Bit system, but Its only a hunch)

Please help,
Thank you,

Simba

---

### Post by Vladlenin5000 on 2015-06-28
No, it has packages for 64-bit...
What you need to do after adding the repository is to update:
```
sudo apt-get update
```
Then you should be able to install.

---

### Post by simba4 on 2015-06-28
Sorry, 

Performed that update before. **I did it now again**.
the update do perform Ok, but then the command: '[COLOR=#800080]**sudo apt-get install whatsapp-purple**[/COLOR]' still responds with '[COLOR=#800080]**E: Unable to locate package whatsapp-purple**[/COLOR]'

maybe there is another command?

Simba

---

### Post by howefield on 2015-06-28
Then there is no package called whatsapp-purple in the repository.

What's the name of the repository you added to get the whatsapp-purple package ?

---

### Post by simba4 on 2015-06-28
Well,

Here is a screenshot of my repository.

It is highly probable that something is wrong there, but I don't know what.
Your knowledge and knowhow is very valuable and I am appreciate it very much,

Thank you,

Simba

---

### Post by howefield on 2015-06-28
There is no whatsapp-purple package in that repository - it only contains the package pidgin-whatsapp.

[https://launchpad.net/~whatsapp-purple/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~whatsapp-purple/+archive/ubuntu/ppa?field.series_filter=trusty)

---

### Post by Vladlenin5000 on 2015-06-28
> **howefield said:**
> There is no whatsapp-purple package in that repository - it only contains the package pidgin-whatsapp.

[https://launchpad.net/~whatsapp-purple/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~whatsapp-purple/+archive/ubuntu/ppa?field.series_filter=trusty)

Indeed. That means the instructions are wrong.0

---

### Post by simba4 on 2015-06-28
Ok,

I'm lost here.
Is there no way to install 'pidgin-whatsapp' (whatsapp-purple)?


[IMG]http://www.livepencil.com/mambers/imagesmem/youremail/emotic/thinking/think01.gif[/IMG]
Simba

---

### Post by howefield on 2015-06-28
> **simba4 said:**
> Is there is no way to install 'pidgin-whatsapp' (whatsapp-purple)?

Of course,

```
sudo apt-get install pidgin-whatsapp
```

will do that, but whether that is the correct package for what you need I don't know, having no interest in whatsapp, I can only answer your original question regarding why you couldn't install whatsapp-purple. The package may simply have been renamed but maybe you could have a look around for a current tutorial whilst you wait for someone who knows more. :)

---

### Post by Vladlenin5000 on 2015-06-28
Actually the package *pidgin-whatsapp* is the one you can install (probably, ... I ain't testing it).
The instructions say to install *whatsapp-purple* which doesn't work because that package isn't  in that PPA. Will it work with the former? I don't know...

---

### Post by bapoumba on 2015-06-28
> **Vladlenin5000 said:**
> Actually the package *pidgin-whatsapp* is t0he one you can install (probably, ... I ain't testing it).
The instructions say to install *whatsapp-purple* which doesn't work because that package isn't  in that PPA. Will it work with the former? I don't know...

I was having a look and came to the same conclusion : [http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu/dists/vivid/main/binary-amd64/Release](http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu/dists/vivid/main/binary-amd64/Release)

---

### Post by simba4 on 2015-06-28
Well,

If they renamed the pack from '[COLOR=#800080]whatsapp-purple[/COLOR]' to '[COLOR=#800080]**pidgin-whatsapp**[/COLOR]', shouldn't I also add the 'new name' to the repository as '[COLOR=#b22222]**deb [http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu](http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu) trusty main**[/COLOR]'?

Ok, I did that, but then, when the repository Reloads, I get 'error 404'...


[IMG]http://www.livepencil.com/mambers/english/youremails/2004/shhh_angel_surp/surprise.gif[/IMG]
Simba

---

### Post by bapoumba on 2015-06-28
[http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu/pool/main/p/pidgin-whatsapp/](http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu/pool/main/p/pidgin-whatsapp/)
The package name is pidgin-whatsapp from what I can see.

---

### Post by howefield on 2015-06-28
> **simba4 said:**
> Ok, I did that, but then, when the repository Reloads, I get 'error 404'...

Not sure why you would be surprised at that, you now querying a non existent repository.

Go to the link I previously posted and click on the "*Technical details about this PPA*" link, you will see the name of the repository.

---

### Post by berto-ar on 2015-07-11
Hello, I have the same problem as simba4, I wish to install whatssap but I can not find a tutorial updated.... simba4 do you finally install whatssap on pidgin? how did you do?

---

### Post by sazawal on 2015-09-05
I have exactly the same problem. The "pidgin-whatsapp" as far as I know was an earlier project which needed a username and password. The password was needed to be sniffed somehow over the local network which was troublesome and I didnt actually try it after installing this package about an year ago. The whatsapp-purple seems to be a new package without a need for password but it is not working according to the instructions given on davidgf's page ([https://davidgf.net/whatsapp/](https://davidgf.net/whatsapp/)).

---

