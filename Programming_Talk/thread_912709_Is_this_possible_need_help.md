---
title: "Is this possible? need help"
date: 2008-09-07
forum: Programming Talk
---

### Post by montamer on 2008-09-07
hi, 
What im trying to do was...... if i show a page with handwritten sentences
(big enough) to webcam connected to pc it must be able to decode the writing on the image to text; and speak through a text to speech application like festival.
i was looking for a handwriting recognition application that will be able to convert the writing on an image(snapshot from camera) to text. Any other suggestions are welcome.

[B]
My intention was to make a system which can read, recognize face and objects(using opencv), understand a few sentences(using sphinx) and talk back. etc..... and finally port all the stuff to a arm board (BeagleBoard) and make a mobile robo :) . I dont know how far can i go, but i would like to give it a shot :).
[/B]

sorry for my english
thanx

---

### Post by LaRoza on 2008-09-07
That is called OCR: [http://en.wikipedia.org/wiki/Optical_character_recognition](http://en.wikipedia.org/wiki/Optical_character_recognition)

Webcams typically have lower resolutions, and OCR applications in my experience don't work well enough with handwriting all the time.

It is a rather complex task.

---

### Post by PaulM1985 on 2008-09-07
I agree with LaRosa.  It is something that I have studied in the past and to compute these things from scratch, it is difficult.  

For example with facial recognition, all faces are slightly different, then there are different angles that the face can be shot at as well as different sizes.  

Handwriting can be quite difficult because you would need to have a basis of characters to run through and handwriting styles can be different, straight or italic, loopy writing or basic.  

I am not sure if software is out already to compute the sorts of things you are interested in, but to do it yourself from my experience, it looks like a large task.

I hope this has been of some help.  Let me know if you manage it, because I would be interested in the results.

Paul

---

### Post by fiddler616 on 2008-09-07
Re Handwriting: No. Selected quotes from the Wikipedia article:
> Systems for recognizing hand-printed text on the fly have enjoyed commercial success in recent years...The algorithms used in these devices take advantage of the fact that the order, speed, and direction of individual lines segments at input are known. Also, the user can be retrained to use only specific letter shapes. **These methods cannot be used in software that scans paper documents, so accurate recognition of hand-printed documents is still largely an open problem.** Accuracy rates of **80% to 90% on neat, clean hand-printed ** characters can be achieved, but that accuracy rate still translates to **dozens of errors** per page, making the technology useful only in very limited applications.

And keep in mind these are professional people hard at work...

---

### Post by Zugzwang on 2008-09-07
Most of the stuff you mentioned is subject of active academic research, and the people working on it didn't get any of that working as it should. You have to be *very* good in order to make something better than that bunch of thousands of professors and an uncountable number of grad students working on it. ;-)

---

### Post by locutus42 on 2008-11-16
if possible, you might try typed sentances instead of handwritten. OCR does far better with typed words. I think Google relesed some code for some OCR software and there are a few text to speach packages in many GNU/Linux repositories and probably some on SourceForge too.

---

### Post by skullmunky on 2008-11-22
so the writing recognition but I'm interested in hearing how far you get with the rest of it, because that's already a fair amount.  like, opencv on the ARM, how's that going?

---

### Post by Tomosaur on 2008-11-23
At one of my old jobs we scanned in forms sent in by people and OCR software read the documents and tried to interpret their handwriting. The way this worked:

1: Sample document is scanned in. The 'sample' is a blank version of the documents which customers will return to us. We would need to mark the areas of the page where hand-writing would be on the real documents, so the OCR software would be able to distinguish between printed text on the page, and handwritten text in the text-boxes.
2: Scan in the real document. OCR software analyses it and presents us with what it thinks the real text says.
3: We have to go through each individual field and make sure the text has been read properly. As someone else said, success rate was usually around 80%, and this is when we asked people to write in block capitals (thus minimising hand-writing differences between thousands of people - most people write capital letters in much the same way).

This is a commercial, enterprise OCR system. Writing your own to recognise any old text is going to be a challenge!

Of course, you could write a program which you would give to your users which would produce an image which you could decode. All you would then need to do is attach a picture of the user's face. As with any project - KISS (Keep it simple, stupid!) applies. Don't make it more difficult than it needs to be!

---

