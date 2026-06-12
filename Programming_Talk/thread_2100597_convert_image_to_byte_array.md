---
title: "convert image to byte array"
date: 2012-12-19
forum: Programming Talk
---

### Post by sanda199 on 2012-12-19
Hi everyone, I am just newbie of ubuntu. I need your precious help. I wanna transfer images from one ubuntu computer to another via tcp/ip socket programming in c language. 

If you have any clues or reference, pls kindly let me know. I'm really appreciate your help. 

Thanks for ur help.

---

### Post by dwhitney67 on 2012-12-19
> **sanda199 said:**
> Hi everyone, I am just newbie of ubuntu. I need your precious help. I wanna transfer images from one ubuntu computer to another via tcp/ip socket programming in c language. 

If you have any clues or reference, pls kindly let me know. I'm really appreciate your help. 

Thanks for ur help.

The clue has been given to you in your other thread with a similar topic.

Now you MUST read the concepts of basic network programming before being spoon-fed an answer to your query.

P.S.  Here's the link, once again, to [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html").

---

### Post by sanda199 on 2013-01-02
Hi everyone, I'm just newbie for ubuntu and programming as well. I would like to ask that how to convert image to byte array and send it to socket via socket programming in c language. If anyone knows some hint, please kindly let me know. Thank you so much for your patience and time :)

---

### Post by TheFu on 2013-01-02
> **sanda199 said:**
> Hi everyone, I'm just newbie for ubuntu and programming as well. I would like to ask that how to convert image to byte array and send it to socket via socket programming in c language. If anyone knows some hint, please kindly let me know. Thank you so much for your patience and time :)


[LIST=1]
[*]Ask the file how large it is
[*]Allocate an array that is that size + 5 bytes.
[*]open the file.
[*]read the file into the allocated array.
[*]close the file.
[*]open a socket to the remote machine.
[*]write the img_array to the socket.
[*]close the socket.
[*]free the array memory AND set the array pointer to NULL to prevent miss-use later.
[/LIST]
On the other side, you'll need a listener. This is all pretty standard stuff with 10,000 of implementations with source code out there. Lots of "C network programming" or "Advanced UNIX Programming" books have examples too.

If this is for a class, fine.  In the real world, you'd probably want lots of error checking and you'd want to work at a slightly higher level than sockets.

---

### Post by dwhitney67 on 2013-01-02
> **sanda199 said:**
> Hi everyone, I'm just newbie for ubuntu and programming as well. I would like to ask that how to convert image to byte array and send it to socket via socket programming in c language. If anyone knows some hint, please kindly let me know. Thank you so much for your patience and time :)

You keep asking for help on this same topic, yet is appears that you have not lifted one finger to get yourself to the level of having developed a single line of code.

What level are you at with respect to programming?  The term "newbie" can mean anything.  If you have zero programming experience, then IMO, you should not be attempting to develop socket-level applications at this time.  You should start with something much more basic.  Get use to using the GCC compiler, and once proficient, then migrate to other complex subjects.

I'm attaching this link to a C-programming tutorial that you may find useful:

[http://beej.us/guide/bgc/output/print/bgc_A4.pdf](http://beej.us/guide/bgc/output/print/bgc_A4.pdf)


For Network programming tutorial, I will include the following link again (I previously posted this in one of your other posts on this same topic):

[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by TheFu on 2013-01-02
> **dwhitney67 said:**
> You keep asking for help on this same topic, yet is appears that you have not lifted one finger to get yourself to the level of having developed a single line of code.

**Thanks for this response.  **I'm here to help people that want to learn for themselves AND realize when they are in over their heads.  

Perhaps if he showed some code that compiles someone could help?

I am not here to write code for others and I doubt that anyone else is either.  **Socket programming is not a good first project** to attempt on Linux, THAT is certain.  A more than basic understanding of IPv4 networking is needed too. Being confused by NAT is not good.  I can only recommend that the OP step back, draw a picture showing what he's trying to accomplish on the network, fill in as many concrete details, then start asking specific questions one-at-a-time and show with code what he's already attempted.

We really are here to help.

---

### Post by howefield on 2013-01-02
Duplicate threads merged.

---

### Post by sanda199 on 2013-01-02
> **TheFu said:**
> 
[LIST=1]
[*]Ask the file how large it is
[*]Allocate an array that is that size + 5 bytes.
[*]open the file.
[*]read the file into the allocated array.
[*]close the file.
[*]open a socket to the remote machine.
[*]write the img_array to the socket.
[*]close the socket.
[*]free the array memory AND set the array pointer to NULL to prevent miss-use later.
[/LIST]
On the other side, you'll need a listener. This is all pretty standard stuff with 10,000 of implementations with source code out there. Lots of "C network programming" or "Advanced UNIX Programming" books have examples too.

If this is for a class, fine.  In the real world, you'd probably want lots of error checking and you'd want to work at a slightly higher level than sockets.



Thanks for your answer. I will try to do it. Thanks

---

### Post by TheFu on 2013-01-03
> **sanda199 said:**
> Thanks for your answer. I will try to do it. Thanks

I should point out that doing this on Windows would have similar high-level steps, though I haven't done any socket programming on Windows since before WinXP was released.

---

