---
title: "*Java* Char array to ascii value"
date: 2007-03-02
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-02
Hello, as I'm learning Java I decided to re-make an old project I've done in vb.net. A very simple, very uncool and extremely easy to decode encryption/decryption program.

Basically, what i'm going to get it to do is to take in the users string, put it into an array, convert it to it's ascii value (For now, later on I'll be doing something simple like multiplying it by 3*10^8(Speed of light, wee) or something like that to make it a little less obvious) and then print it to the screen (In succession, not on line at a time). 

However, I'm have a tad bit of trouble doing this in java and I cannot really find an example on the net that fulfills my needs. So, I'm turning to you Java programmers out there in hopes that you could help a nubby little bugger like myself :P

So, this is how I've declared my character array, I'm not sure if you need it or not...

char [] arrayEncrypt = plainText.toCharArray();

So, I'm thinking it's going to be something simple as arrayEncrypt.toasciivalue or something that seems so obvious... Or it won't be and my confusion might just be justified. 
I'll release the full program when I've found out to do this, finish off the code and then work out the decryption method. Also, I'll need to learn how to read and write to a text file. but, something like that i'm sure if well documented in numerous places, so I'll just google it. 

Thanks for any and all help that you could possible give.

---

### Post by Ramses de Norre on 2007-03-02
```
for(int i=0;i<arrayEncrypt.length;i++)
{
    System.out.println((int)arrayEncrypt[i]);
}
```

---

### Post by Darkness3477 on 2007-03-02
Yeah, I worked out how I can convert it to the ASCII value for printing, but I want to actually have it stored in an array (int array, not char now it's been converted) so that I can print it to a file and/or do a little math to it to make it a little less obvious that it's ascii code. 

I hope I'm making sense here. I often don't

---

### Post by Ramses de Norre on 2007-03-02
```
char[] arrayEncrypt=s.toCharArray();
int[] intArray=new int[arrayEncrypt.length];

for(int i=0;i<arrayEncrypt.length;i++)
{
    intArray[i]=(int)arrayEncrypt[i];
}
```

---

### Post by Darkness3477 on 2007-03-02
Hey, thanks. I just worked out I could do what i wanted to do without creating the new int array, but I'm glad you showed me. It would have annoyed me not knowing.

if i seem a little thick right now, it's 'cause it's 3:09 AM. Anyway, thanks. Now it's time to get to decrypting it, and then reading and writing it to a file. That'll be an experience and a half, no doubt.

---

### Post by Ramses de Norre on 2007-03-02
The java IO system is quiet horrible the first time you see it, but you get used to it ;)
And another cool way to encrypt is ROT13, the first 13 characters of the alphabet are shifted 13 places forward, the latest 13 letters are shifted 13 places backwards.
It's not too hard to code it in java.

---

### Post by Darkness3477 on 2007-03-02
Ah, yeah. I'm pretty much just doing this to get used to the basic stuff. the IO system looks a little confusing. Getting user input is kinda confusing for me. I know what to do, not exactly sure why I have to do it... But, I'll get it one day when I could actually be stuffed to look into it.

This ROT13 seems pretty cool. However, right now I just want to get my simple method of converting it to ASCII, then doing... well, this... ascii value * 3 + 3 / 2 + 1.... First numbers and what nots that came to my head. 

Already, doing the simple things that I have done now, i've learnt a reasonable ammount. Also, I still need to write some code for error checking (Like checking to make sure the user actual inputs a serious of characters) and make a simple consol type menue. Most likely, type 1 for .... 2 for .... But, that should serve it's purpose as an education excercise. 

Thanks again for your help.

---

### Post by Ramses de Norre on 2007-03-04
Using 3/2 will cause trouble, first of all if you use int 3/2==1. And if you use doubles you'll need to be very very careful with the results due to floating point restrictions. You're working on a computer...

For input, have you looked into the scanner class? It's very useful for input, you can get input from the command line with an object like this: ```
Scanner *name*=new Scanner(System.in);
```

---

