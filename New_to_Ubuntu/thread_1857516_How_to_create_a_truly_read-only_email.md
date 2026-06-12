---
title: "How to create a truly read-only email?"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by swarup on 2011-10-10
Is there any email application available in Ubuntu, in which one can send an email which will be able to be read but not edited? And if someone wants to make a copy of the text or essay or article contained therein, only the entire article (and not parts of it) can be made a copy of, and that copy should also be uneditable. 

These days, normal email cannot be edited-- but the text in it can be highlighted, pasted somewhere into another document, and then edited.

But for example, if someone makes a scan of an article and sends it out as an email attachment, then people can read the scanned article but cannot edit the texts which that scan contains. In a similar way, within the email application itself i.e. without using a scanner, can this be done? Or another example-- there are websites where one cannot highlight the text and copy it. Is there a similar facility in email? And, I do not wish to send out the essay as an attachment either-- for, many people are afraid to open attachments. So, the article should be in the body of the email. And yet only copyable as a whole, and uneditable.

---

### Post by WasMeHere on 2011-10-10
You can make copying harder showing your document as *images* of the pages (e.g. lossless png or lossy jpg), but screendumps and OCR scanning would probably produce text to be edited.

A related topic is *signature*. If someone edits a signed document, the signature check will produce an error message. This can be done in Thunderbird with the Enigmail plug-in.

---

### Post by swarup on 2011-10-10
> **Olle Wiklund said:**
> You can make copying harder showing your document as *images* of the pages (e.g. lossless png or lossy jpg), but screendumps and OCR scanning would probably produce text to be edited.

I will research this. But can you let me know in brief, is this facility provided within the email program itself? For example, in evolution (which I use), is there a command to turn one's email into an image or lossless png format?

> **Olle Wiklund said:**
> A related topic is *signature*. If someone edits a signed document, the signature check will produce an error message. This can be done in Thunderbird with the Enigmail plug-in.

Does that mean that in Thunderbird if this is done, the text of the email will be unable to be copied/pasted, say, into a word processor? The signature check will not allow this to be done? Or does it rather mean that it can be done but if done, then the "signature check" in the original email will some show that it has been tampered or something?

---

### Post by WasMeHere on 2011-10-10
> **swarup said:**
> I will research this. But can you let me know in brief, is this facility provided within the email program itself? For example, in evolution (which I use), is there a command to turn one's email into an image or lossless png format?

No, email is ***text*** media. Actually attachments are converted to text strings and decoded at reception. So you have to use attachments. An alternative is to upload your document (in whatever format (image, pdf ...) to a web-site and link to it in your email.

> **swarup said:**
> 
Does that mean that in Thunderbird if this is done, the text of the email will be unable to be copied/pasted, say, into a word processor? The signature check will not allow this to be done? Or does it rather mean that it can be done but if done, then the "signature check" in the original email will some show that it has been tampered or something?
Only that it can be checked whether it has been tampered or not, but also that it really comes from ***you***.

---

### Post by HermanAB on 2011-10-10
You can try laser engraving the text on a tungsten plate.  That will make it rather hard to edit, but you may have some difficulty sending it by email then...

The best you can do is ensure verification and deniability.  If you sign the email with GPG, then readers can verify that it really was you that wrote it.

---

### Post by WasMeHere on 2011-10-10
clarification: enigmail in thunderbird is using gpg

---

### Post by swarup on 2011-10-10
> **Olle Wiklund said:**
> Only that it can be checked whether it has been tampered or not, but also that it really comes from ***you***.

I see. So it sounds like there really is no way to make an email uneditable or the material it contains unalterable. The best one can do is make it so that recipients can be assured that the text is still just as it was when originally sent by me-- i.e. if someone forwards the email to another, it will contain the signature. But even there i.e. in the signature scenario, someone can simply highlight and copy the text from the email, create an entirely new email or wordprocessor file, edit as desired, and sent out to others without there being any trace of my original email or its signature. Is it not the case?

> **Olle Wiklund said:**
> No, email is ***text*** media. Actually attachments are converted to text strings and decoded at reception. So you have to use attachments. An alternative is to upload your document (in whatever format (image, pdf ...) to a web-site and link to it in your email.

ok-- so if I upload my document to a website and link to it in my email, what is the best format in which to create the document i.e. so that it will be uneditable by others? The document itself as well as any copies of it, should be uneditable. Can image files or pdf files achieve this?

---

### Post by snowpine on 2011-10-10
If the document can be displayed on a computer screen, then it can be edited.

Simply take a screenshot and edit in GIMP.

Sorry. :(

---

### Post by collisionystm on 2011-10-10
Well I have a ridiculous idea. 

Write an email. print it. Photograph yourself with the email. Record on a video camera the process of putting it in a envelope, stamping and placing in mailbox. Then filming the postman picking it up. When he picks it up ask him to show is credentials and employee ID to the camera and speak clearly. 

That should give you enough proof to show our original in the event of an edit.

OR.... just blind copy someone else upon sending? The time stamps will match up if you have to prove anything.

---

### Post by swarup on 2011-10-10
1. Up until now I was thinking that if you take a screenprint of a text document and email the screenprint to someone, they won't be able to edit it. Say there is such a screen print, of the text of this very forum thread. If you can you import the screenprint into GIMP, then what sort of changes can be made to the screenprint? i.e. just ruin the image by introducing other objects onto it, or in a very fine way can certain words in the screenprint image be changed-- in such a way that no one could tell the words had been changed?

2. When one creates a blogsite, the option is given at the time of creation whether one desires it to be a copyable site, or "read-only". If one selects "read-only", then what is achieved by that? Will visitors to the blog be able to highlight and copy text from the blogsite?

---

### Post by snowpine on 2011-10-10
> **swarup said:**
> 1. Up until now I was thinking that if you take a screenprint of a text document and email the screenprint to someone, they won't be able to edit it. Say there is such a screen print, of the text of this very forum thread. If you can you import the screenprint into GIMP, then what sort of changes can be made to the screenprint? i.e. just ruin the image by introducing other objects onto it, or in a very fine way can certain words in the screenprint image be changed-- in such a way that no one could tell the words had been changed?

2. When one creates a blogsite, the option is given at the time of creation whether one desires it to be a copyable site, or "read-only". If one selects "read-only", then what is achieved by that? Will visitors to the blog be able to highlight and copy text from the blogsite?

1. Your document can be edited in any conceivable way using GIMP/Photoshop/etc. If it is done by an expert then it will be undetectable.

2. Anyone can highlight and copy text from any website, give it a try yourself! :)

---

### Post by haqking on 2011-10-10
> **snowpine said:**
> 1. Your document can be edited in any conceivable way using GIMP/Photoshop/etc. If it is done by an expert then it will be undetectable.

2. Anyone can highlight and copy text from any website, give it a try yourself! :)

+1

you have no control over what someone else can do or does to something that you are no longer in receipt of.

---

### Post by swarup on 2011-10-10
Here I am attaching a screenprint of a website. Can one of you bring it into GIMP and change a few words of text, and repost it to this thread. Please inform me which words have been changed. I would like to see how well this can be done. 

Is it something that anyone with a small bit of experience can manage well? Or are the "experts" we are talking about difficult to come by, who can alter a screenprint so no one will know?

The documents I will be sending are simple plain text documents. But I am sending this screenprint as just an example, so I can understand what it is that can be done.

---

### Post by swarup on 2011-10-10
snowpine, You mention that "Anyone can highlight and copy text from any website".

What about [this]("http://chetangole.com/blog/wp-copyprotect/") website, for example, where it is claimed that the plugin will prevent anyone from doing copy-paste from your blog. Here below are the first few lines from the site. Does it work?


> Protect your blog content from theft.

use WP-CopyProtect

Many bloggers are facing the problem of content theft. Content theft is a really serious problem, and it must be dealt with. We bloggers write our posts using much effort, and “Copy Cats” simply copy our content without our permission, and without attribution.

That’s why I developed a simple, but powerful, plug-in which will protect your digitally-written work on your blogs. This plug-in is based on the technique of “Disabling right-click” and “No text selection” scripts.

This plug-in will

    * Disable right click on your blog.
    * Disable Text selection.
    * will not affect SEO. Search engines can read your content without any problem..


---

### Post by snowpine on 2011-10-10
> **swarup said:**
> snowpine, You mention that "Anyone can highlight and copy text from any website".

What about [this]("http://chetangole.com/blog/wp-copyprotect/") website, for example, where it is claimed that the plugin will prevent anyone from doing copy-paste from your blog. Here below are the first few lines from the site. Does it work?

Keep reading:

> Please note

This is just a basic copy protect plug-in, if someone want to copy your content he/she can go to source of the blog and can easily copy the stuff from there.

And of course this plugin will not prevent a screenshot.

Care to enlighten us what this is all about? :)

---

### Post by haqking on 2011-10-10
> **swarup said:**
> snowpine, You mention that "Anyone can highlight and copy text from any website".

What about [this]("http://chetangole.com/blog/wp-copyprotect/") website, for example, where it is claimed that the plugin will prevent anyone from doing copy-paste from your blog. Here below are the first few lines from the site. Does it work?

They cant prevent a screen shot and them image manipulation

---

### Post by swarup on 2011-10-10
> **snowpine said:**
> Keep reading:



And of course this plugin will not prevent a screenshot.

Care to enlighten us what this is all about? :)


1. What does he mean by "the source of the blog"?

2. (reply to your question) I am wanting to publish my teacher's teachings-- and I don't want them to be altered in any way. The goal is that all should be able to read freely, but nobody can alter what is written. I want the integrity of the material to be maintained.

3. If not in ubuntu, then in any other OS or using any software, or applying any password protection, is it possible to issue text in any format such that it cannot be changed? (meaning neither the original, nor a copy of it)

4. How about the screenprint I sent. Can someone show me what a change would look like?

---

### Post by snowpine on 2011-10-10
> **swarup said:**
> 2. (reply to your question) I am wanting to publish my teacher's teachings-- and I don't want them to be altered in any way. The goal is that all should be able to read freely, but nobody can alter what is written. I want the integrity of the material to be maintained.

No technological method exists to prevent a reader from copying/altering/sharing your teacher's teachings, if you choose to publish them on the World Wide Web. 

Depending on where you live, your country may have Copyright laws that prevent someone from stealing/altering the text.

---

### Post by swarup on 2011-10-10
> **snowpine said:**
> No technological method exists to prevent a reader from copying/altering/sharing your teacher's teachings, if you choose to publish them on the World Wide Web. 

Depending on where you live, your country may have Copyright laws that prevent someone from stealing/altering the text.

I see. But still, the reason I sent the screenprint was

1) I would like to know how much of a complex job it is to do something like this. The more complex it is to do, the less likely it is to happen.

2) When you change a word or two, I would like to see whether it is evident or not. And if it is evident, then how distorted the appearance is. 

That is, is it something the general public can easily do with a bit of interest, or is it highly specialized work. 

Please if you can, give me a sample using the screenprint I sent. :)

---

### Post by haqking on 2011-10-10
> **snowpine said:**
> No technological method exists to prevent a reader from copying/altering/sharing your teacher's teachings, if you choose to publish them on the World Wide Web. 

Depending on where you live, your country may have Copyright laws that prevent someone from stealing/altering the text.

+1

however copyright does not prevent someone from doing it, just makes it illegal and gives grounds for legal action.

The altering and stealing can still take place ;-)

---

### Post by Lisiano on 2011-10-10
Changes are under Hot Topics 1st from PTIN to PIN and the 2ns, the word e-file to e-filth. Should be enough.

As for the source.
I removed the ads, some stuff and replaced the forms and hot topics stuff. Basically you can do this to whole web page. Note: I am not a web designer NOR a photoshoper/gimper
As people have said, anything published on the Web is editable. Even a photo of a printed scan of a book. That will require skill but yes, still possible.

As for the Wordpress plugin, some users run a plugin called NoScript, it will stop that plugin from doing anything. As for converting text to a image, there is OCR which will recognize converted stuff 100%, worse performance for scanned stuff.

Thus the only thing you can really do is just sign the email to make it so that it is know that it is coming from you, beside that, you can't do anything that will be a sure-fire method.

---

### Post by SeijiSensei on 2011-10-10
The best I can think of is to create a PDF of the text and send it with an MD5 or SHA1 signature.  If the recipient's copy doesn't hash to the same value, it's different.

Frankly I can't imagine why this is even a concern. I used to teach university.  Nothing I said was so brilliant that it needed to be set in stone.

---

### Post by swarup on 2011-10-10
> **Lisiano said:**
> Changes are under Hot Topics 1st from PTIN to PIN and the 2ns, the word e-file to e-filth. Should be enough.

As for the source.
I removed the ads, some stuff and replaced the forms and hot topics stuff. Basically you can do this to whole web page. Note: I am not a web designer NOR a photoshoper/gimper
As people have said, anything published on the Web is editable. Even a photo of a printed scan of a book. That will require skill but yes, still possible.

As for the Wordpress plugin, some users run a plugin called NoScript, it will stop that plugin from doing anything. As for converting text to a image, there is OCR which will recognize converted stuff 100%, worse performance for scanned stuff.

Thank you so much for the screenprints. That is really helpful to see. 

When you say that a printed scan of a book requires skill, is the difference there that you changed only two words, whereas in a book scan there are many more words and thus the volume of work multiplies because of that?

Each word I guess requires effort, right? So if someone wanted to replace an entire sentence or paragraph with another, it might take quite a bit of work right? 

The reason I ask is that the likelihood of someone tampering would be expected to go down dramatically as the time involved to do so goes up.

Last question: What about languages written in different scripts, like Chinese or Indian scripts. Most of my texts are in Indian language scripts. Does that change things at all when it comes to the challenges involved in changing/editing/adulterating documents placed on the web or sent as image format via email?

---

### Post by WasMeHere on 2011-10-11
> **swarup said:**
> ...
The reason I ask is that the likelihood of someone tampering would be expected to go down dramatically as the time involved to do so goes up.

Yes

> **swarup said:**
> 
Last question: What about languages written in different scripts, like Chinese or Indian scripts. Most of my texts are in Indian language scripts. Does that change things at all when it comes to the challenges involved in changing/editing/adulterating documents placed on the web or sent as image format via email?
One difference is the font/character (a complicated font takes more work), another difference is how many people know the language.

Also you could have a picture on the background (like on money bills) instead of a plain colour. This makes it more time-consuming to change the text without leaving ugly traces.

But I do not understand why you want this. It should be sufficient to attach an electronic signature so that people can check whether the document is original or if it has been tampered with: *gpg, md5sum, shasum*, there are many alternatives.

Have fun finding your way to do it :-)
Olle

---

### Post by HermanAB on 2011-10-11
BTW, with Gimp or Photoshop, you can zoom in untill you can edit the individual pixels.  Obviously then you can do *anything* to the picture, given enough time and coffee.

---

### Post by Lars Noodén on 2011-10-11
> **swarup said:**
> 2. (reply to your question) I am wanting to publish my teacher's teachings-- and I don't want them to be altered in any way. The goal is that all should be able to read freely, but nobody can alter what is written. I want the integrity of the material to be maintained.

Then sign it with PGP.  That way visitors can verify that it is unchanged.  

As others have mentioned, there are no technical ways to prevent copying, and such ideas [don't work even in theory](http://www.zdnet.com/news/why-drm-wont-ever-work/152278).  However, you can publish it under [licensing](http://creativecommons.org/licenses/by-nd/2.0/) which would require that it can be copied only if the copies are verbatim copies.  That combined with the PGP signature are probably your best bet.  People are obligated by law to follow the license.  Look at the [CC BY-ND](http://creativecommons.org/licenses/by-nd/2.0/) license for one example.

---

### Post by swarup on 2011-10-14
Many thanks to all who wrote on this thread-- it has been tremendously helpful. I shall mark this thread as "solved" at this time, and experiment with some of the modalities suggested. Should there be further questions at that time, I'll again write back. Again, thanks to all. :)

---

