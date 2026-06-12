---
title: "Q about basic encryption (AES)"
date: 2013-03-09
forum: Programming Talk
---

### Post by ironic.demise on 2013-03-09
I'm trying to learn.
I'm trying to encrypt/decrypt data using ' 128 bit AES, ECB mode, Zero byte padding'
The data itself is 64 16-byte blocks (RFID)(16 "sectors"/4 blocks=1 sector)

The key itself is the MD5 hash of the following 0x56 bytes:
<first 0x20 bytes of sector 0> <1-byte block index>  
<0x35-byte constant> 
 
unsigned char hashConst[] = {  
        0x20, 0x43, 0x6F, 0x70, 0x79, 0x72, 0x69, 0x67, 0x68, 0x74, 0x20, 0x28, 0x43, 0x29, 0x20, 0x32, 
        0x30, 0x31, 0x30, 0x20, 0x41, 0x63, 0x74, 0x69, 0x76, 0x69, 0x73, 0x69, 0x6F, 0x6E, 0x2E, 0x20, 
        0x41, 0x6C, 0x6C, 0x20, 0x52, 0x69, 0x67, 0x68, 0x74, 0x73, 0x20, 0x52, 0x65, 0x73, 0x65, 0x72, 
        0x76, 0x65, 0x64, 0x2E, 0x20}; 


What's the unsigned char hashConst stuff?
What's a 1-byte block index?
What's a 0x35-byte constant?
                                       (0x35=64)? 64 byte constant?

There's also some instructions to (after performing 2 CRC16 checksums on some data stored on the chip) to "increment area sequence by 1" before performing a third CRC16 checksum, what does this mean?

I've been trying my best to figure out how this specific set of data is encrypted, decrypted and such but, it's gotten very confusing.
If any more information is needed, I'd be able to show you all of the instruction I have, I'd appreciate if anybody can help dumb down these instructions for me.

---

### Post by ironic.demise on 2013-03-09
Don't let me down community ;)

---

### Post by trent.josephsen on 2013-03-09
People on here have lives too (or so I imagine); don't get worked up over no response, especially after only an hour on what is a Saturday afternoon in the US.

That said, you haven't made a great start because I'm still unsure what you're trying to do. What language are you using? C? That snippet, which you have provided no context for, looks like C.

I would imagine the block index is the number corresponding to which block you're encrypting; i.e. you would encrypt block 0 with the index set to 0, then encrypt block 1 with the block index set to 1, etc. until you have encrypted all 64 blocks.

"some data stored on the chip" -- what chip? Is this an embedded application of some kind? Does it have something to do with RFID?

You convey the impression of having a handful of instructions but no goal or purpose in mind. Start with what you're trying to achieve and maybe we can help you figure out what questions you really need to ask.

---

### Post by ironic.demise on 2013-03-09
Don't mean to sound pushy, I'm in no rush.
Yeah this is for RFID.
Yeah, that snippet is in C, I actually have the source code for an application I'm looking at which I'm trying to figure out how it works, because it doesn't do exactly the thing I need.

The program takes the encrypted data, decrypts it and edits a few specific blocks before encrypting it again and writing it back to the chip.
The chips are used in a specific program and need to be encrypted that way for it to work.

I don't know C, so I'm currently reading through the source code without much knowledge, but slowly working out what is otherwise a basic program.
On a 1k card, I want to to take the data, edit a different set of blocks to the aforementioned program, and write it back, so I'm trying to deduce the encryption so I can write a program of my own.

This way I can learn some programming, and get my head around some RFID/NFC hardware all at once.

I "COULD" use the program mentioned, but firstly, it doesn't work with my hardware, and secondly, it's Windows only.

So, I can't get it working with my hardware and I don't want to use windows as this specific project is on the Raspberry pi.


I could buy the specific hardware needed for like $20, but... that's no fun.



So, where his program edits block 0x08 and 0x24... I only want to edit block 0x00 and 0x01
But, I don't know the encryption required.

---

### Post by lemonoid on 2013-03-10
i imagine the second post due to if nobody responds in 3 seconds the post gest pushed 5 pages back. i do the same thing. its not getting worked up i promise. this is a very active forum. i've had plenty of the same issues and it helps to bump. obviously, as there is a response :) sorry just my input as i've had the same issue. fun fun fun. this community can provide help on anything so when someone comes here they have to stay on top of their threads.

---

### Post by trent.josephsen on 2013-03-10
At the time of ironic.demise's second post, the thread was at the top of the page. Programming Talk is not the Absolute Beginners Section and it takes a few days for a new post to stop getting new views. Besides, if you're going to bump something, you should at least add some new information -- "this is what I found out so far", "here's the code I'm working on -- can anybody point out my mistake", even "These are the search terms I Googled; what else should I look for?" Making a new post just to comment on the lack of replies is simply counterproductive from a discussion point of view.

@OP, not mad at you :) You say you're reading through the source code of a C program, but you don't know C? Well... you can't really do that. I mean, you can, but you can't expect to learn much. It might work with Python or Lua, but for anything non-trivial in C I think you really need to know the language first.

You don't mention whether you already know any other programming languages; if you do, learning C will be much easier. If you're new to programming entirely... maybe you'd be better off working on some other project for a while.

Do you have to use C? I mean, if you already understood exactly what your program has to do, could you write it in another language or do you need to modify the existing program?

---

### Post by ironic.demise on 2013-03-11
> **trent.josephsen said:**
> At the time of ironic.demise's second post, the thread was at the top of the page. Programming Talk is not the Absolute Beginners Section and it takes a few days for a new post to stop getting new views. Besides, if you're going to bump something, you should at least add some new information -- "this is what I found out so far", "here's the code I'm working on -- can anybody point out my mistake", even "These are the search terms I Googled; what else should I look for?" Making a new post just to comment on the lack of replies is simply counterproductive from a discussion point of view.

@OP, not mad at you :) You say you're reading through the source code of a C program, but you don't know C? Well... you can't really do that. I mean, you can, but you can't expect to learn much. It might work with Python or Lua, but for anything non-trivial in C I think you really need to know the language first.

You don't mention whether you already know any other programming languages; if you do, learning C will be much easier. If you're new to programming entirely... maybe you'd be better off working on some other project for a while.

Do you have to use C? I mean, if you already understood exactly what your program has to do, could you write it in another language or do you need to modify the existing program?

I don't have to use C, it's just that I know that C has the encryption algorithm inside, so I'm just reading through specifically the MD5 functions and looking at the math.

I don't know any "real" programming languages, I've built websites using html, php and mysql and I can use bash well enough that I get by.
I know I can't just "figure" out C, so I've been reading about the commands he's been using and reading some C tutorials (although, so far most of it is the obvious stuff)

I could write it in Bash, because Bash can access the hardware, and bash can use libnfc if I remember correctly.
It's just that unless I figure out how to calculate an MD5 hash to use as a key in the encryption, I won't be able to use it in the end.

Sorry, but reading through his notes on how to understand all this is still a bit alien to me even though he covered virtually everything.

---

### Post by trent.josephsen on 2013-03-11
Ok, well, I'm still not 100% on the end-to-end here, but there are definitely utilities that could help you if you wanted to do it in bash. For instance, you can use echo and md5sum to get the md5 hash of an arbitrary sequence of bytes:

```
$ echo -n "<First 20 bytes><Block index>\x20\x43\x6F\x70\x79\x72\x69\x67\x68\x74\x20\x28\x43\x29\x20\x32\x30\x31\x30\x20\x41\x63\x74\x69\x76\x69\x73\x69\x6F\x6E\x2E\x20\x41\x6C\x6C\x20\x52\x69\x67\x68\x74\x73\x20\x52\x65\x73\x65\x72\x76\x65\x64\x2E\x20" | md5sum
3f7c1ad6f62ecec304c872fc3766bcd0  -
```
Obviously you'd have to do more work to substitute the actual content at the beginning of the message, but that's beyond my bash skills (all the bash I need to know is just enough to invoke perl).

I notice the apparently random string of bytes is actually a copyright notice. I don't know if what you're doing or plan to do qualifies as a copyright violation, but it's definitely something to be aware of.

Cheers

---

### Post by ironic.demise on 2013-03-12
> **trent.josephsen said:**
> Ok, well, I'm still not 100% on the end-to-end here, but there are definitely utilities that could help you if you wanted to do it in bash. For instance, you can use echo and md5sum to get the md5 hash of an arbitrary sequence of bytes:

```
$ echo -n "<First 20 bytes><Block index>\x20\x43\x6F\x70\x79\x72\x69\x67\x68\x74\x20\x28\x43\x29\x20\x32\x30\x31\x30\x20\x41\x63\x74\x69\x76\x69\x73\x69\x6F\x6E\x2E\x20\x41\x6C\x6C\x20\x52\x69\x67\x68\x74\x73\x20\x52\x65\x73\x65\x72\x76\x65\x64\x2E\x20" | md5sum
3f7c1ad6f62ecec304c872fc3766bcd0  -
```
Obviously you'd have to do more work to substitute the actual content at the beginning of the message, but that's beyond my bash skills (all the bash I need to know is just enough to invoke perl).

I notice the apparently random string of bytes is actually a copyright notice. I don't know if what you're doing or plan to do qualifies as a copyright violation, but it's definitely something to be aware of.

Cheers

Good stuff, thanks for the input.

I know about the copyright, and don't worry, I'm not doing anything illegal, I just found some information the internet and thought I'd have a deeper look myself.
I'm not about to do anything that violates copyright. I might take another look just to be sure, however I'm not even that sure on what I'm doing yet so it's no biggie.

I'm not bad with bash, I could probably do more.

I'm just wondering now how it would be easiest to pull information out of an rfid dump in bash, without just using grep to search out specifics.

---

### Post by ironic.demise on 2013-03-12
> **trent.josephsen said:**
> Ok, well, I'm still not 100% on the end-to-end here, but there are definitely utilities that could help you if you wanted to do it in bash. For instance, you can use echo and md5sum to get the md5 hash of an arbitrary sequence of bytes:

```
$ echo -n "<First 20 bytes><Block index>\x20\x43\x6F\x70\x79\x72\x69\x67\x68\x74\x20\x28\x43\x29\x20\x32\x30\x31\x30\x20\x41\x63\x74\x69\x76\x69\x73\x69\x6F\x6E\x2E\x20\x41\x6C\x6C\x20\x52\x69\x67\x68\x74\x73\x20\x52\x65\x73\x65\x72\x76\x65\x64\x2E\x20" | md5sum
3f7c1ad6f62ecec304c872fc3766bcd0  -
```
Obviously you'd have to do more work to substitute the actual content at the beginning of the message, but that's beyond my bash skills (all the bash I need to know is just enough to invoke perl).

I notice the apparently random string of bytes is actually a copyright notice. I don't know if what you're doing or plan to do qualifies as a copyright violation, but it's definitely something to be aware of.

Cheers

Great!
Now I know I can grab the first 32 bytes (0x20),the block id and the code provided for the md5sum

However, whilst terminal would use \x as the syntax for hexadecimal... I'm wondering whether I should precede with #,\x or 0x?
# is the symbol I see used the most in day to day use.
\x is the "technically" correct symbol for bash (and C languages from what I read)
However by reading the source code, and from the snippet of hex above, it seems that 0x00 would yield the correct md5?

---

### Post by trent.josephsen on 2013-03-12
\x00 is interpreted by bash. 0x00 is C. If you tried to use 0x00 in the command I gave, you'd get the md5sum of the four-byte string {'0', 'x', '0', '0'} which is not at all the same thing as the md5 of the single byte { 0 }.

You'd use 0x00 instead if you were writing a C program that printed the string to stdout. (Although you could use \x00 as well, inside a string or character constant: '\x00'.)

As far as I know, # is only used for HTML color codes. I've never used a programming language that interpreted such a string (like #00) as a number in hex.

---

