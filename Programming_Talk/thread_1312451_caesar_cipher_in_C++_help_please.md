---
title: "caesar cipher in C++ help please"
date: 2009-11-03
forum: Programming Talk
---

### Post by crofty23 on 2009-11-03
hey guys im new to the forum even though i have been using ubuntu for a while now, I have to create a caesar cipher in C++ Given an input string and a number,x,between 1and 12, as an excersize in my IT course. im finding it really difficult as i have only previously coded in Visual Basic.
 
the excersize states [FONT=Cambria]
[LEFT] [/LEFT]
[/FONT]does anybody have any ideas on the pseudocode or source code that i could use to get started on this basic program?
 
thankyou in advance!

---

### Post by Arndt on 2009-11-03
> **crofty23 said:**
> hey guys im new to the forum even though i have been using ubuntu for a while now, I have to create a caesar cipher in C++ Given an input string and a number,x,between 1and 12, as an excersize in my IT course. im finding it really difficult as i have only previously coded in Visual Basic.
 
the excersize states [FONT=Cambria]
[LEFT] [/LEFT]
[/FONT]does anybody have any ideas on the pseudocode or source code that i could use to get started on this basic program?
 
thankyou in advance!

You have to understand the requirements first. Then do a small example by hand and then it will be easier to formulate pseudo-code.

How do you encrypt "Hello!" with number 11, for example? And, how do you decrypt it?

(Why only 1 to 12?)

---

### Post by Tony Flury on 2009-11-03
Clearly your message needs to be bigger then the cryptography key (i.e. your 1 to 12) and depending on definition a key of 1 might be pointless.

Bear in mind that the whole Point of Pseaudo code is that it is language independent. So your Pseudo code for Visual basic will be similar to your pseudo code for C++. The end implementation will be different of course, but the Pseudo code will be similar.

NB1 : We don't do your homework here - so unless you show you are trying to do the work yourself you wont find anyone who will give you source code or even Psuedo code - what would you learn if someone else gives you the answer.

---

### Post by crofty23 on 2009-11-04
thankyou for the replies. i'm not looking for someone to crete this program for me because this would not be beneficial to me, 
 
what I would like someone to do, is to suggest what data types and processes need to be written, to create this program. I would like actual pseudocode if possible.
 
plus i don't think pseudocode is acually going to affect my learning since its just structured english

---

### Post by Arndt on 2009-11-04
> **crofty23 said:**
> thankyou for the replies. i'm not looking for someone to crete this program for me because this would not be beneficial to me, 
 
what I would like someone to do, is to suggest what data types and processes need to be written, to create this program. I would like actual pseudocode if possible.
 
plus i don't think pseudocode is acually going to affect my learning since its just structured english

It works better the other way: you supply the pseudo-code and an attempt of coding, and you get help with the details of implementation. Once you're there, improvements in the algorithm, and logical errors will also be suggested.

Exactly how is your task phrased? Paste it in here. Does it explain what a Caesar cypher is? If not, have you looked it up?

---

### Post by crofty23 on 2009-11-04
sorry i should of explained more lol basically the user inputs a message (String) and inputs the offset of the shifting of the letters.
 
the message is basically output again but with the shifting in place.
 
caesar cipher is a simple encyption technique that basically shifts letters of the alphabet by an offset of what the user types in. the range i need is 1-12. e.g. a offset of 4 A = E. 
 
i guess now I have tried to explain this to you, now I have something to go from!

---

### Post by Arndt on 2009-11-04
> **crofty23 said:**
> sorry i should of explained more lol basically the user inputs a message (String) and inputs the offset of the shifting of the letters.
 
the message is basically output again but with the shifting in place.
 
caesar cipher is a simple encyption technique that basically shifts letters of the alphabet by an offset of what the user types in. the range i need is 1-12. e.g. a offset of 4 A = E. 
 
i guess now I have tried to explain this to you, now I have something to go from!

Since you have previously coded in Visual Basic, I suggest you write the program first in Visual Basic, and then convert it to C++. As someone else wrote, the logic will be similar. Then Visual Basic will serve as pseudo-code for you.

Does the specification say what to do with non-letters, such as "!"?

---

### Post by ve4cib on 2009-11-04
> what I would like someone to do, is to suggest what data types and processes need to be written, to create this program

The only data types you really need to deal with are strings and chars.  For this particular application I'd be tempted to use C-Strings (which are nothing more than null-terminated char arrays), but that's more of a personal choice.  You could use the C++ String class if you're more comfortable with that.

As for what processes (?? I assume you mean functions?) you need to write, the easiest way I can think to break it up is...

1- main: just calls the other stuff
2- readPlaintext: gets the input message from the user (either through stdin or a file, depending on the assignment spec)
3- getKey: get the Caesar Cipher key from the user (again, either through stdin or another file)
4- encrypt: encrypt the plaintext using the specified key
5- decrypt: decrypt the ciphertext using the specified key

Main would look something like this:

```
def main():
    key = getKey()
    plainText = getPlainText()

    print "Encrypting\n",plaintext,"\nwith key",key

    cipherText = encrypt(plainText,key)
    print "Encrypted:\n",cipherText

    plainText2 = decrypt(cipherText,key)
    print "Decrypted:\n",plainText2

    if(plainText2==plainText):
        print "Plaintexts match.  Huzzah, it works!"
    else:
        print "Plaintexts differ.  We apparently screwed something up"

```

That's all I'm going to give you, I'm afraid.  None of the meaty parts have been implemented, but seeing how main could be laid out should hopefully give you some ideas about what you need to do.

Obviously there are lots of other ways the program could be laid out.  This is just one possible way to get the gears turning.

---

### Post by crofty23 on 2009-11-04
thanks for all the help, this will help alot. i will keep you posted on how it goes.

---

