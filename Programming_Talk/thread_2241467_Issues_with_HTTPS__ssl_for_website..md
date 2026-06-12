---
title: "Issues with HTTPS / ssl for website."
date: 2014-08-26
forum: Programming Talk
---

### Post by hockey97 on 2014-08-26
Hi, I am having trouble playing videos on my website. It works fine in HTTP but doesn't load at all in HTTPS. 

I have it in a .avi file format. My website is using a self-signed SSl cert.

---

### Post by ofnuts on 2014-08-27
Does the rest of the site work in HTTPS? Is the video streamed?

---

### Post by hockey97 on 2014-08-27
Yes, the video is streamed and the whole website works in HTTPS. 

It's just that the videos won't work only in HTTPS. In HTTP it works fine.

There's no errors... the headers respond in both cases with a status code of 200 meaning it's ok.

I use a self-signed certificate. I was told that this might be the cause of the problem. 

The problem isn't with the code. The code runs fine. I mean everything works in HTTP.
So, the code works but it has to do something with the media and the protocol HTTPS.

---

### Post by SeijiSensei on 2014-08-27
Is it even worthwhile to bother encrypting a video stream?  Just use HTTP.

---

### Post by hockey97 on 2014-08-27
Well I want all my traffic on my website encrypted.  It's due to ranking on google. They recently made changes that now websites that use solely HTTPS  will have a higher rank. It's to encourage websites to be secure. That is what google said:

[http://googlewebmastercentral.blogspot.com/2014/08/https-as-ranking-signal.html](http://googlewebmastercentral.blogspot.com/2014/08/https-as-ranking-signal.html)

---

### Post by SeijiSensei on 2014-08-27
Are you sure it matters if things like streams are also encrypted?  That would be a dumb policy since encrypting a stream degrades performance.  I'd bet that using HTTPS for the pages but not for the streams would work for Google.

I never care about Google rankings since they wouldn't lead anyone to my low-traffic sites anyway.  What matters most is how many other sites link to yours; I have few of those.

---

### Post by hockey97 on 2014-08-27
> **SeijiSensei said:**
> Are you sure it matters if things like streams are also encrypted?  That would be a dumb policy since encrypting a stream degrades performance.  I'd bet that using HTTPS for the pages but not for the streams would work for Google.

I never care about Google rankings since they wouldn't lead anyone to my low-traffic sites anyway.  What matters most is how many other sites link to yours; I have few of those.

Well Google says now part of their rankings algorithm will check your whole website for HTTPS. If  anything like a image or video doesn't use HTTPS. It will hurt your rankings. 

They claim that it's a security and privacy issue whey you don't encrypt the connections. 

I am more for security and privacy. I would like to have my users knowing the traffic between my server and them is encrypted or protected from others eavesdropping on what is being transferred.

---

### Post by ofnuts on 2014-08-28
Yes but you can have streaming clients that don't know/expect how handle HTTPS. You may have to choose between your ranking or your customer base...  And frankly, I don't think that the encryption will change your ranking much. Do you expect Wikipedia, UbuntuForums or StackExchange to be dropped from Google search results?

---

### Post by hockey97 on 2014-08-28
No, they won't drop them from the database. They will rank them lower. They're trying to make the internet a safer place. Their website is secure. Now the problem they face is websites that are in their database that don't use safe practices. They pretty much said they want to see every website use HTTPS by 2016. 

So, the websites that use HTTPS will have a higher rank then places like ubuntuforms.org if they don't use HTTPS. YOU would still be listed. It's just that you won't be the first one that pops up.  They said by 2016 If the website isn't using HTTPS by then they will weed them out. It's an effort on their part to make the internet safe and harder for hackers to do anything. That is their goal.

---

### Post by ofnuts on 2014-08-29
So they will drop WIkipedia, and poeple will find that other search sites give better search results...

In the meantime, the choice you have is a site with a high ranking and pissed-off users, or a lower-ranking site with happy users, more likely to reference your site.

---

