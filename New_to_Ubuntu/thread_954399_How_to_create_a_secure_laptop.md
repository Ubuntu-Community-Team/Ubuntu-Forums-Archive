---
title: "How to create a secure laptop?"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by kramer65 on 2008-10-21
Hello,


I want to buy a netbook in a couple months and use it for fairly sensitive data (unfortunately no world domination plans yet, but simple work related stuff). I heard about the encrypted folder feature which comes with Ubuntu 8.10 which I will be very happy with. 

The only problem is that passwords which I do want to save in firefox are saved outside of the encrypted folder. This means that anybody can still enter my system by [resetting the password]("http://www.hackszine.com/blog/archive/2008/09/howto_reset_a_lost_ubuntu_pass.html") and read out my passwords in firefox. Is there a way to avoid this risk?


ps. I suddenly notice that I think that your encrypted drive is save when people use that method. Am I right in this?

---

### Post by woodenbrick on 2008-10-21
I think Truecrypt gives you the ability to encrypt an entire partion with an os inside, though I never used it for this purpose.
[http://www.truecrypt.org/]("http://www.truecrypt.org/")

---

### Post by kosmiciatakuja on 2008-10-21
Sure there is, and I'm doing this right now. Although I'm not using 8.10 yet so I have to create my encrypted folder by myself. But that this an easy task, I use EncFS, you can follow the guide here ([http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)) and create an encrypted folder anywhere. 

And to mount this encrypted folder you have to input a password of your choice, so even if somebody resets your password, or gets root access to your system, they still need this password to open your encrypted directory, and as far as I could check there is no way around this (except brute force attack, or dictionary attack which will quickly succeed if you have a simple, short password!). 

Now, how to encrypt Firefox data? 
First, I created an 'encrypted' directory in my home dir (~/encrypted). 
Second, there is a '.mozilla' directory in your home dir. If you enter it, there should be a 'firefox' subdir. Under 'firefox' there is some strange named directory like 'sl39skds.default' which stores all your information from firefox (like passwords, history, forms, everything). I simply moved that directory to ~/encrypted thus making it secure and then created a symbolic link to it with something like:
```
ln -s ~/encrypted/sl39skds.default ~/.mozilla/firefox/sl39skds.default
```

and now you just have to mount the directory with EncFS (or whatever directory encryption you use) before using firefox (to prevent it from creating a new profile or something when it doesn't find the data it expects). I have the mounting of encrypted directory added to my 'autostart' in xfce and simply enter my password after I log in. 

Hope this helps, let me know if you have questions!
Piotr

---

### Post by kramer65 on 2008-10-21
Wow! Now that is an answer I was dreaming of!

I was initially just looking whether it was possible at all. But appearently it is.. :-)

So what I need to do is:
1. Use the encrypted folder feature introduced in ubuntu 8.10
2. Move the firefox profile directory there
3. Create a symbolic link from the firefox directory to my encrypted directory
4. Run the mounting of the encrypted directory with the startup.

I will wait for the 8.10 release to use the encrypted folder. I hope you don't mind but I have time so I rather wait for that.

Also, does that mean that the password for the protected directory could/should be different from your login password? And then I would need to enter two passwords everytime I login; one for logging in, and one for mounting the encrypted directory right? (It would be fine to enter two passwords but I just wonder about it..)

---

### Post by kosmiciatakuja on 2008-10-21
Yes, the steps you outlined are good! Just one clarification from my side: when I spoke about mounting the directory and entering the password, I spoke about EncFS, the encryption tool I'm using currently in 8.04. The new encrypted folder feature in 8.10 might be improved in that you will not have to enter the password twice, I don't know about that as I haven't checked it out yet. 

In any case, the general procedure should be similar: just move the firefox profile (the one with the strange name) directory to your encrypted dir and then symlink it where it was originally. That should work, just make sure you never start firefox without the encrypted dir open and ready. 

I think it's a wise idea to wait for 8.10 and the new feature since it will probably be much easier to use than doing it by hand with EncFS. 

Also, the comment above about encrypting the whole disk/partition is valid too! But there are some considerations like performance and so on to take into account when you're encrypting whole partitions. 

And, as the final note, I did the same to thunderbird (encrypting everything I have there) since my company email is also sensitive and needs to be protected. The procedure is exactly the same, except that the thunderbird profile dir (with some other strange name) is under ~/.mozilla-thunderbird in my case.

---

