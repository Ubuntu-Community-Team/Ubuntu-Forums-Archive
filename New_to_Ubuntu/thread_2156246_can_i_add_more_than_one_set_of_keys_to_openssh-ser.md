---
title: "can i add more than one set of keys to openssh-server?"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by Psil0cybin on 2013-06-21
Hello guys So im following a youtube tutorial [http://www.youtube.com/watch?NR=1&feature=fvwp&v=HCXDaGIgjcQ](http://www.youtube.com/watch?NR=1&feature=fvwp&v=HCXDaGIgjcQ) on getting my SSH shell to work with only keys and not a password, thus decreasing my chances of getting my shell taken over  by brute force attempts.
I was wondering if It was possible to get more than one set of keys, because following the video you copy your public key into the home folder, and than add it to the authorized_keys file...would I then delete the public key and reupload another one, once again adding it to my authorized_key files, thus allowing me to have two computers connecting?
Using this command?

cat id_rsa.pub >. ~/.ssh/authorized_keys (would this command, add the pub file to the authorized_key file or overwrite it? I am wondering this because I do not want to replace the keys just add another one to the list)

Thanks in advance
Psil0

---

### Post by newbie-user on 2013-06-21
Using a single > will overwrite a file's contents. Using two >> will append the file. So if you wanted to add additional public keys to your authorized_keys file, you would:

```
cat id_rsa_second_key.pub >> ~/.ssh/authorized_keys
```

---

### Post by agillator on 2013-06-21
What newbie-user said is correct. However, something you said makes me think you really don't understand the process yet. Perhaps I can help you there and it will help you even more down the road. SSH does not allow a COMPUTER to connect to the server, but allows a USER on another computer to connect to the server. This is why it is so important to keep your private key private. You do not have to delete your public key, in fact you shouldn't. You can use it as many times and in as many places as you wish. It is public, after all. Here's roughly how the sign-in process works. User sends a message to server 'I am user and I want to sign in'. Server sends a message to user which consists of a random string encrypted by user's public key which server gets from the authorized keys file. The only thing that can decrypt the string is user's private key, which is why it MUST be kept private. So, user decrypt's the string and encypts it again using user's private key so only user's public key can decrypt it. Server decrypts it and compares it to the original string. If it matches, then user is who he says he is. Of course the whole world can decrypt it because the public key was used. But that is ok because the whole world doesn't know the private key and cannot send that string to the server enrypted by the private key. Note no keys have been exchanged during the process. Now there is one more step. The server knows the user is who he says he is, but does the user know the server is who he says HE is? No. So the entire process is gone through again by the user taking a random string, encrypting it with the server's public key from the known_hosts file and sending it. The server decrypts it, encrypts it with it's private key and sends it back. The public key decrypts it so the user now knows the server is not some interloper. Now, the link is established and communication is encrypted by each using the other's public key so no one else can decrypt it since only the private keys can decrypt. Note that if you have two computers you can use the same private key on each and then sign in to the server from either.

---

### Post by Lars Noodén on 2013-06-21
Another way to add a key to your *authorized_keys* file is to use a text editor.

```

nano -w ~/.ssh/authorized_keys

```

Just be sure when you add the public key to that file that you have it whole and unbroken on a single line.  

When you make the keys, you can use the -f option with [ssh-keygen](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh-keygen.1.html) to name them whatever you want.

```

ssh-keygen -f ~/.ssh/another_rsa_key  -t rsa -b 2048 

```

If the key is to be used for only one task, you can add *command="foobar"* to the beginning of the line in ~/.ssh/authorized_keys where 'foobar' is a command.  Then when the key is used it will launch that command when it connects and when the command is finished, it will disconnect.

---

