---
title: "what does this mean and how can i resovle it"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by blake7 on 2008-09-30
W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A
thank you for your time

---

### Post by binbash on 2008-09-30
you have to import the key

---

### Post by blake7 on 2008-09-30
yea cheers for that, what is a key and how do i inport it

---

### Post by ellalan on 2008-09-30
Try this in Terminal
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

HTH.

---

### Post by SupaSonic on 2008-09-30
Type this in the terminal
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

---

### Post by SupaSonic on 2008-09-30
> **ellalan said:**
> Copy this in Terminal:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Then,  "sudo apt-get update" in terminal. HTH.

Why medibuntu? I thought he needed a key from this wicd thing.

---

### Post by wilsong on 2008-09-30
It appears that you might have been trying to do an update, and that site you listed 

GPG error: [http://apt.wicd.net](http://apt.wicd.net) gutsy   

was in your repositories. GPG is a security program, that generates keys, public and private.  Your probably missing the latest GPG public key that Apt uses for signature checking. 

You might want to use apt-key 

# wget | apt-key

# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv-keys 1F41B907 ; gpg &#8211;export 1F41B907 | apt-key add -;


but use the key that your in requirement of, the server might be the same or different depending on where your repositories are coming from. this is a general example.


Or trying the example exactly above this, my example was more generic.. :)

---

### Post by blake7 on 2008-09-30
well which one should i do

---

### Post by wilsong on 2008-09-30
I would recommend running 

```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```


check page 2 , i added more, just dont like the forms its hard to see that theres more pages, hope you find what i said.

---

### Post by blake7 on 2008-09-30
nope it say dir not found

---

### Post by wilsong on 2008-09-30
Try 



```
wget -q http://apt.wicd.net/wicd.gpg
```

then try 

```
sudo apt-get add wicd.gpg 
```

then try to redo whatever you did to get that message

---

### Post by zxscooby on 2008-09-30
what were you trying to do when you got this error? An update?

---

### Post by blake7 on 2008-09-30
yes i was updating

---

### Post by wilsong on 2008-09-30
Did you try the last thing i said to try? I never heard back, about trying to do it in two separate steps?

---

### Post by zxscooby on 2008-09-30
typing 

```
sudo apt-get upgrade --allow-unauthenticated
```

will ignore authentication and allow the download of packages
without checking to make sure they are secure.

---

### Post by blake7 on 2008-09-30
what do you mean two seperate steps , i press return then add in the other what else can you do?

---

### Post by blake7 on 2008-09-30
i get this when i tryed thoes to commands

E: Invalid operation add

---

### Post by zxscooby on 2008-09-30
i think he meant ```
sudo apt-key add wicd.gpg
```

---

### Post by Elfy on 2008-09-30
If this command ```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
``` isn't working please give us the output. It works ok for me, are you typing or pasting it.

---

### Post by blake7 on 2008-09-30
yes he did you are all stars, thanks for your time.

and have a good one

---

### Post by wilsong on 2008-09-30
> **zxscooby said:**
> i think he meant ```
sudo apt-key add wicd.gpg
```

Ahh yes Sorry about that I did make a typo. I am glad this finally worked for you tho! Dont get discouraged, and dont give up!  

I can understand how frustrating this new stuff can be, just get passionate, read all you can about stuff, and of course if you have a question and want a quick easy answer! Ask the forum ;)

---

### Post by serimp on 2008-09-30
Blake7, look at this thread:

[http://ubuntuforums.org/showthread.php?t=933985&highlight=wicd+NO_PUBKEY](http://ubuntuforums.org/showthread.php?t=933985&highlight=wicd+NO_PUBKEY)

I had the same problem and fixed it like that.
Sergio

---

### Post by greybeard95a on 2008-10-01
[I can't find an option to delete this post.  I found this thread from a Google search and did not notice quickly enough that this was the third page.]

---

