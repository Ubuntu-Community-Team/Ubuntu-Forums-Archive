---
title: "Life Hacker guide 2011 Setting up a server"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by 90Ninety on 2012-12-29
Okay basically this is my other attemp at following another user friendly guides to building a Server - see link [http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu]("http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu")

 I have installed 12.10 Ubuntu x64 

I have also tried other guides but have tripped up on them ( see other posts if interested . Anyhow I have managed to progress more successfully with this guide, the following is an extract from the guide , this was my last successfull step 
> **LAST STEP TAKEN **Lastly, you'll need to create a password for all of those shared drives, so you can access them from any computer (and so other people can't). To do this, just open up a terminal and type the following, replacing whitsongordon with your own username:
 sudo smbpasswd -a whitsongordon 
Then type and re-type a password of your choice when prompted.

 Ok done that , now the next step really is a jump and allmost seems to be missing something 
> **NEXT STEP** Now, head over to your main computer and check to see if the folder was shared properly. On Windows, open up Windows Explorer and click on "Network" in the left sidebar. Your server should show up in the list, and if you double click on it, you'll be asked for a username and password. 


 Who , what, when, how ? Why all of a sudden would windows find my server ? Via an Ip address I wonder , am I missing something , ?

---

### Post by Cheesemill on 2012-12-29
Windows queries the network for any available computers.

If you've set up Samba properly then your server will reply to this request

---

### Post by 90Ninety on 2012-12-29
> **Cheesemill said:**
> Windows queries the network for any available computers.

If you've set up Samba properly then your server will reply to this request

So  Mr Cheese do you vouch for life hacker guide ?

---

### Post by Cheesemill on 2012-12-29
I've never seen it before, I always use the official documentation.
[https://help.ubuntu.com/](https://help.ubuntu.com/)

As long as you know how to edit a text file it should be all you need.

---

### Post by 90Ninety on 2012-12-29
The life hacker guide does not mention configuring samba at all ,  is this guide a complete solution for setting up a server ?  

Or is configuring Samba a MUST to enable networking ?

---

### Post by Cheesemill on 2012-12-29
You are configuring samba using the lifehacker guide, but you are using nautilus to do so by right-clicking on a file and changing the sharing properties.

I've never tried this method as my servers don't have a GUI.

---

### Post by 90Ninety on 2012-12-29
Hmm using the right-click nautilus  sharing  method I get the following error 


'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Unexpected information received.

Any suggestions ?

Have solidly spent the last two days of my holiday trying to get this up and running , is this normal?

---

