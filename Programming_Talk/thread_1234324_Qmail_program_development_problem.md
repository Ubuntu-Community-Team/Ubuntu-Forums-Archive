---
title: "Qmail program development problem"
date: 2009-08-07
forum: Programming Talk
---

### Post by alexx88 on 2009-08-07
Hello!

I have some problems developing an application to work with Qmail. To be more precise, I have created a program that receives through a pipe different email files (one for every run of the program). I have almost no experience using Qmail (but I am working on it :) ) so please excuse any non-technical language in speaking about it. Anyway, when I redirect the emails from a file to the program ,everything works like a charm, but when I switch the file for Qmail, my program crashes every time with the following error: " Aack,_child_crashed._(#4.3.0)/  "

At the end of the message I posted a link to the program (you can compile it with make) and some email examples. After doing some testing it seems that the problems come from the getenv() and testURL functions. While the getenv problems seems fixable I can't understand how can the testURL function affect the functioning of Qmail.

 How the program works:
It receives the email by a pipe. It parses the content looking for the subject line and saves it. Then it searches for a user/pass pair and saves them as well. Using a base URL it builds an "extended" URL. 

The problems appear when it tries to test the validity of this URL by making a HTTP request to the webserver. I must say again that the program works perfectly when data is coming from a file and not from Qmail. 

I think that it's all a conflict on the network lever between the two processes, but I don't know for sure. In any case, I will continue to try finding the cause by myself, but I could really use some help, please.

Program + exemples: [http://www.2shared.com/file/7057786/9f8 … Qmail.html]("http://www.2shared.com/file/7057786/9f8d8fd8/program_Qmail.html")
Password: ubuntu_qmail


Thank you!
Alex

---

