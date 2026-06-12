---
title: "Access text file on the net with C++"
date: 2010-01-10
forum: Programming Talk
---

### Post by shababhsiddique on 2010-01-10
Is it possible to access any text file on the internet (direct download link) ? just like ofstream accesses.

file located at =
[http://download749.mediafire.com/xkxdm0mebe9g/tdxyedl1zfd/words](http://download749.mediafire.com/xkxdm0mebe9g/tdxyedl1zfd/words)

//its a text file, decided not to put any extension.

I am trying to achieve this =
    
   * read a line of text (just like  "x.getline()" )
   * put it on a string variable

Please help..
Note: Please try to keep things simple and easy.

---

### Post by Zugzwang on 2010-01-10
The simplest thing is probably to use some library, like libcurl.

A usage example is given here: [http://www.luckyspin.org/?p=28](http://www.luckyspin.org/?p=28). Also look here: [http://curl.haxx.se/libcurl/c/libcurl-tutorial.html](http://curl.haxx.se/libcurl/c/libcurl-tutorial.html)

---

### Post by shababhsiddique on 2010-01-11
> **Zugzwang said:**
> The simplest thing is probably to use some library, like libcurl.

A usage example is given here: [http://www.luckyspin.org/?p=28](http://www.luckyspin.org/?p=28). Also look here: [http://curl.haxx.se/libcurl/c/libcurl-tutorial.html](http://curl.haxx.se/libcurl/c/libcurl-tutorial.html)

Thanks for your reply. I am looking to it. hope it works...

---

### Post by shababhsiddique on 2010-01-11
What am I doin wrong? I cant compile my source code.. I cant compile event this one -

[http://www.luckyspin.org/?p=28](http://www.luckyspin.org/?p=28)

the error is somewhat similar to Nick. 
I have downloaded and installed curl. Installation went fine, still prompts.
curl/curl.h no such directory

---

### Post by Zugzwang on 2010-01-11
If for something you want to install, there exists a package, install it using the package manager whenever possible. This is the case here. So you installed the package libcurl3-dev or libcurl4-gnutls-dev or libcurl4-openssl-dev? Then, the error message shouldn't appear.

Also note that you will need to tell your linker that you want to link against the library. How to do so depends on your environment (type of Makefile, IDE, etc.).

---

### Post by shababhsiddique on 2010-01-11
> **Zugzwang said:**
> If for something you want to install, there exists a package, install it using the package manager whenever possible. This is the case here. So you installed the package libcurl3-dev or libcurl4-gnutls-dev or libcurl4-openssl-dev? Then, the error message shouldn't appear.

Also note that you will need to tell your linker that you want to link against the library. How to do so depends on your environment (type of Makefile, IDE, etc.).

I am using C++ code::blocks IDE in Ubuntu jaunty. How should I link?

---

### Post by Zugzwang on 2010-01-11
> **shababhsiddique said:**
> I am using C++ code::blocks IDE in Ubuntu jaunty. How should I link?

Add "libcurl" or "curl" (never used that IDE myself) as a library to link against in the project options.

---

### Post by shababhsiddique on 2010-01-11
I dont get the library link... somehow the error showed previously has changed(maybe after updating libcurl i did it it was less than a Kb)...

no it says -

undefined reference to curl_easy_xxxx



well I found a linker setting tab under my compiler settings. Which file should I add to the list? 

may be some functions used by curl

---

### Post by Zugzwang on 2010-01-11
> **shababhsiddique said:**
> well I found a linker setting tab under my compiler settings. Which file should I add to the list? 


As I said, link "curl" to the program. See attachment for a screenshot.

---

### Post by shababhsiddique on 2010-01-11
_[]("http://www.luckyspin.org/?p=28")_finally managed to run the program without errors.

what should happen if I run this program?
[http://www.luckyspin.org/?p=28](http://www.luckyspin.org/?p=28)


I dont seem to get it. sorry to ask such question...plz help everyone needs to learn

---

### Post by Zugzwang on 2010-01-11
> **shababhsiddique said:**
> I dont seem to get it. sorry to ask such question...plz help everyone needs to learn

Have a look at the comment in the first lines of the program. They tell you roughly what it is supposed to do. Note that the URL of the stuff to retrieve is taken from "argv[1]", i.e., the first option given to the program when running. As far as the meaning of all the curl commands is concerned, have a look at the official tutorial, whose URL I've given a few posts ago.

---

### Post by shababhsiddique on 2010-01-11
> **Zugzwang said:**
> Have a look at the comment in the first lines of the program. They tell you roughly what it is supposed to do. Note that the URL of the stuff to retrieve is taken from "argv[1]", i.e., the first option given to the program when running. As far as the meaning of all the curl commands is concerned, have a look at the official tutorial, whose URL I've given a few posts ago.

thanks very very much for your reply(s) I apreciate your help. Just cant say how much happy I am. cURL is indeed a cool thing..

by the way . .   

I replaced argv[1]'s with the url"www.google.com" and put out the conditions .. now I can see the html code of google!

My target was to view the text file from download link..
[http://download749.mediafire.com/xkxdm0mebe9g/tdxyedl1zfd/words](http://download749.mediafire.com/xkxdm0mebe9g/tdxyedl1zfd/words)

 which does not seem to be possible. Maybe either i need to put out my text as a website or download the file first to HD and then simply open it the old way. 

Is there any way I can access a hosted .txt file from the file hosting sites?

thanks again for your kind help...

Should I mark this thread as solved? [the thread question is not solved yet I think]

---

