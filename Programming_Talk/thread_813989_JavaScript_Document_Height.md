---
title: "JavaScript Document Height"
date: 2008-05-31
forum: Programming Talk
---

### Post by Verminox on 2008-05-31
I need some help in configuring the height of the document in a web application before printing it.

I want to print it on a paper that is 6 inches long. The printer has a roll of paper so it will never run out of paper but unfortunately the hardware is such that it can only print X pages (eg. 6 inches, 12 inches) and not just 8 inches and stop.

Therefore, if the content is long enough to be around 1.5 pages long, I want to append some random text at the bottom (maybe a Quote of the Day or something) so that the excess whitespace doesn't look bad. (This is the client's request so I don't have a choice)

Now, I know JavaScript and DOM fairly well, but I don't know the right way of assessing the height of the document and making the decision of whether or not to append the extra text. 

I've found 3 DOM methods, clientHeight(), offsetHeight() and scrollHeight() which should return the height in pixels but I don't know if this is the right way to go. Also, how would I go about converting pixels to inches? Usually, this is a property of the monitor size and the screen resolution, but what about in a printer?

---

### Post by LaRoza on 2008-05-31
> **Verminox said:**
> 
I want to print it on a paper that is 6 inches long. The printer has a roll of paper so it will never run out of paper but unfortunately the hardware is such that it can only print X pages (eg. 6 inches, 12 inches) and not just 8 inches and stop.

Therefore, if the content is long enough to be around 1.5 pages long, I want to append some random text at the bottom (maybe a Quote of the Day or something) so that the excess whitespace doesn't look bad. (This is the client's request so I don't have a choice)


Web pages + Web browsers + Printer = Fail.

You are making things hard on yourself for no reason. Whitespace isn't bad, and attempting to fill whitespace without good reason leads to a mess.

Perhaps you can have a standard footer and print that on the last page of everything. If this end text is on a new page, discard it, otherwise, it will be on the end of the last page (or first, if there is one) if there wasn't a lot of text.

---

### Post by Verminox on 2008-06-01
> **LaRoza said:**
> Web pages + Web browsers + Printer = Fail.

You are making things hard on yourself for no reason. Whitespace isn't bad, and attempting to fill whitespace without good reason leads to a mess.

Perhaps you can have a standard footer and print that on the last page of everything. If this end text is on a new page, discard it, otherwise, it will be on the end of the last page (or first, if there is one) if there wasn't a lot of text.

That's fine, but how do I 'discard' it automatically? The application operator doesn't want to bother himself with screwing around with Print settings or Page Setup even (probably because there will be a lot of prints per hour). So how do I 'discard' the footer if it is going to be the only thing on another page?

---

### Post by LaRoza on 2008-06-01
> **Verminox said:**
> That's fine, but how do I 'discard' it automatically? The application operator doesn't want to bother himself with screwing around with Print settings or Page Setup even (probably because there will be a lot of prints per hour). So how do I 'discard' the footer if it is going to be the only thing on another page?

I obviously don't know the setup you have. I imagined a person physically excluding it during the collating stage.

The thing is, that this goal is making things hard for no apparent reason. Why exactly does extra whitespace matter (besides the trivial part about not being the most economical use of paper, but if that mattered, these documents would be emailed and not printed)?

Also, remember that this is a webpage, and that the "height" of it is the height of the open browser, it will change. 

I don't know how well supported it is, but you could look into the printer specific CSS (although it won't do anything selectively)

---

### Post by Verminox on 2008-06-01
> **LaRoza said:**
> I obviously don't know the setup you have. I imagined a person physically excluding it during the collating stage.

The thing is, that this goal is making things hard for no apparent reason. Why exactly does extra whitespace matter (besides the trivial part about not being the most economical use of paper, but if that mattered, these documents would be emailed and not printed)?

Also, remember that this is a webpage, and that the "height" of it is the height of the open browser, it will change. 

I don't know how well supported it is, but you could look into the printer specific CSS (although it won't do anything selectively)


By all means, I'm for the whitespace. Unfortunately, the guy who is going to use the application doesn't like it. Well, I think I'll just go tell him to either live with the whitespace, or change the printer to those that print variable length and stop at the end of content. 

Thanks anyway though.

PS: If I have a continuous roll of paper loaded into the printer, and I set top/bottom margins to 0 in the Page Setup, then will the multiple pages look like one continious print?

---

### Post by LaRoza on 2008-06-01
> **Verminox said:**
> By all means, I'm for the whitespace. Unfortunately, the guy who is going to use the application doesn't like it. Well, I think I'll just go tell him to either live with the whitespace, or change the printer to those that print variable length and stop at the end of content. 

Thanks anyway though.

PS: If I have a continuous roll of paper loaded into the printer, and I set top/bottom margins to 0 in the Page Setup, then will the multiple pages look like one continious print?

Tell him that it was scientifically proven to facilitate usability if whitespace was maximised and was utilized during the production stage of development (I have been reading Dilbert, but if it works, let me know)

As for your second question, put things in perspective, I have trouble getting my HP Deskjet F380 to print envelopes correctly. Do you really want me to give advise on that printer's use?

---

### Post by Verminox on 2008-06-01
> **LaRoza said:**
> Tell him that it was scientifically proven to facilitate usability if whitespace was maximised and was utilized during the procuction stage of development (I have been reading Dilbert, but if it works, let me know)

As for your second question, put things in perspective, I have trouble getting my HP Deskjet F380 to print envelopes correctly. Do you really want me to give advise on that printer's use?

:lolflag: I dislike hardware <_<

---

