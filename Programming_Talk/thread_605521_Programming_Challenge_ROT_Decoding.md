---
title: "Programming Challenge: ROT Decoding"
date: 2007-11-07
forum: Programming Talk
---

### Post by samjh on 2007-11-07
Time for a programming challenge, methinks. :)

---------------------------------------------------------------------

An undercover officer has intercepted a cypher-text of a message sent by a wanted terrorist cell.  He has also obtained from a source what is believed to be the cypher-text of that message.

The source claims that the terrorist cell is using the Caesar cypher to encrypt its messages.

Those fools think their messages are secure!

Your first mission, should you choose to accept it, is to create a program that will read the plain-text and cypher-text of the messages we have obtained, and determine the shift parameter of the Caesar cypher.

Your second mission, is for your program to be able to decrypt any Caesar-cyphered message with a user-specified shift parameter.

For assistance, we have uncovered this top secret file for you:
[http://en.wikipedia.org/wiki/Caesar_cipher](http://en.wikipedia.org/wiki/Caesar_cipher)

Good luck!

---------------------------------------------------------------------

Plain text:
> FARSI WILL DRIVE BOMB INTO CAR PARK.  MAY HE BE GRANTED 77 VIRGINS FOR THIS GREAT DEED!

Cypher text:
> YTKLB PBEE WKBOX UHFU BGMH VTK ITKD.  FTR AX UX ZKTGMXW 77 OBKZBGL YHK MABL ZKXTM WXXW!

---

### Post by bfhicks on 2007-11-08
*laugh* When I first read this, I thought it wanted to decrypt the cypher'd text without a plain text document. I was thinking ... "need dictionary, blah blah.." then I realized this is just a simple homework assignment.

---

### Post by bfhicks on 2007-11-08
I wasn't going to post to help you out, but I realized that was kind of mean.

So, i'll pseudo code it for you:
```

First Part:

Make a char array for all 26 letters.

Read in first character from first file.
Read in first character from second file.

Determine shift.


--
Second part:

Store all letters into a char array.

Find it's index in your previously defined alphabet array.
Apply shift, and get index value of original alphabet.
Store new character into new array or plug into current one.

Print out.

Done.


```

---

### Post by aks44 on 2007-11-08
> **bfhicks said:**
> then I realized this is just a simple homework assignment.

*ROFLMAO*

Bad, bad samjh trying to trick people into doing his/her own homework under the disguise of beginner challenges... ;) </irony>


@bfhicks: you're new here, ain't ya? :p



EDIT:
> **bfhicks said:**
> I wasn't going to post to help you out, but I realized that was kind of mean.

So, i'll pseudo code it for you:
How generous of you... :D

---

### Post by samjh on 2007-11-08
Err... thanks for the help, Bfhicks.

Unfortunately, I finished my degree three years ago. :)

Come to think of it, I'd forgotten about this challenge.  Better get a crack on it...

---

