---
title: "Libre Office PDF"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-04-07
Some times when pdfs created with Libre Office (in Linux) is opened in acrobat reader in windows, it either cannot be opened / gives some errors. Though that same pdf can be opened in acrobat in Linux. What can be a good way to ensure that pdfs created are universally readable.

---

### Post by rmil on 2012-04-07
Check the name of the file. Sometimes if you have some non English characters in the name of the file windows adobe reader create error on opening for some reason

---

### Post by terrykiwi83 on 2012-04-07
what version of libreoffice and ubuntu are you using?

---

### Post by 3dmatrix on 2012-04-07
Ubuntu 11.10 + LibreOffice 3.4.4 

The name of the file has no non-english character but the content (text) in the file may have.

---

### Post by SeijiSensei on 2012-04-07
Don't use spaces in the file name either.

I've created a lot of PDFs with OO/LO and sent them to non-Linux people without a problem.  

If you think it might have to do with character sets, make a couple of simple files with and without the non-English characters and try opening them in Windows with Acrobat Reader.  As always when it comes to computer issues, experimentation is the best approach to finding a solution.

---

### Post by 3dmatrix on 2012-04-07
That files opens in Windows (acrobat reader) in my computer but it does not opens when i send it to others.
Another file gives error when i open it in a public windows comp seems its a font prob ! Can it be so ?

---

### Post by SeijiSensei on 2012-04-07
Perhaps.  What if you install the ttf-mscorefonts package on your Ubuntu machine and create the documents with an MS font like Times New Roman or Arial?

---

### Post by vasa1 on 2012-04-07
> **SeijiSensei said:**
> Perhaps.  What if you install the ttf-mscorefonts package on your Ubuntu machine and create the documents with an MS font like Times New Roman or Arial?

But then what about Linux users who may not have the ttf-mscorefonts package installed? Do you know of a font that's common to most systems? Won't that be better for troubleshooting?

---

### Post by SeijiSensei on 2012-04-07
I'm not convinced he's having a font problem in the first place, but his goal seems to be creating PDFs that can be read in Windows.  If so, using a Windows font for testing is a good place to start.

My understanding is that PDFs are designed to be cross-platform so it shouldn't matter what fonts are used.

I don't have a Windows machine handy to see what fonts might be common to both platforms.  Perhaps Century Schoolbook or the Lucida fonts?  I have a rather extensive set of Microsoft fonts that I've maintained over the years and install them on all my Linux boxes so I can't tell what was native and what wasn't at this point.

---

### Post by 3dmatrix on 2012-04-08
> **SeijiSensei said:**
> I'm not convinced he's having a font problem in the first place, but his goal seems to be creating PDFs that can be read in Windows.  If so, using a Windows font for testing is a good place to start.

My understanding is that PDFs are designed to be cross-platform so it shouldn't matter what fonts are used.

I don't have a Windows machine handy to see what fonts might be common to both platforms.  Perhaps Century Schoolbook or the Lucida fonts?  I have a rather extensive set of Microsoft fonts that I've maintained over the years and install them on all my Linux boxes so I can't tell what was native and what wasn't at this point.

In fact i am not interested in using Ms Fonts bcoz i wish to have the independence of using which ever font i wish to and that is why i send my docs in pdf format so that it can be opened in any OS and still look the same.

---

### Post by Zill on 2012-04-08
3dmatrix:  You might like to check the PDF Options for embedded fonts under the "File, Export as PDF" menu.

Specifically, see if the "PDF/A-1a" checkbox is selected.

> PDF/A-1a
Converts to the PDF/A-1a format. This is defined as an electronic document file format for long term preservation. All fonts that were used in the source document will be [COLOR="Red"]embedded[/COLOR] into the generated PDF file. PDF tags will be written.

---

### Post by 3dmatrix on 2012-04-08
> **Zill said:**
> 3dmatrix:  You might like to check the PDF Options for embedded fonts under the "File, Export as PDF" menu.

Specifically, see if the "PDF/A-1a" checkbox is selected.

Thanx i know abt this but i am still not sure if the problem is at all related to fonts or not !

---

### Post by vasa1 on 2012-04-08
> **3dmatrix said:**
> Some times when pdfs created with Libre Office (in Linux) is opened in acrobat reader in windows, it either cannot be opened / gives some errors. Though that same pdf can be opened in acrobat in Linux. What can be a good way to ensure that pdfs created are universally readable.

Does the **exact same file** sometimes open and sometimes not open?

Perhaps you could share some sample pdfs using Google Docs?

---

### Post by 3dmatrix on 2012-04-08
> **vasa1 said:**
> Does the **exact same file** sometimes open and sometimes not open?

Perhaps you could share some sample pdfs using Google Docs?

Yes i sent some files created with Firefox and all of them openeed at the receiving end but the one made with Liber Office did not.

Where as all of them opened in the Xp partition on my comp.

Have prob accessing Google Docs from where i live :) its 'blocked' !

---

### Post by aura7 on 2012-04-08
One of the best approach according to me is to install Open Office. I still use open office due to libre office issues. Libre Office is relatively newer and buggy ( it recently got out of the beta).

---

### Post by 3dmatrix on 2012-04-08
> **aura7 said:**
> One of the best approach according to me is to install Open Office. I still use open office due to libre office issues. Libre Office is relatively newer and buggy ( it recently got out of the beta).

Well ! Open office is fine but i felt this was a minor prob and som compatibility issues might have been raising such errors :) In fact its always Windozzzz machines which have all the errors ready to pop up !

---

### Post by Zill on 2012-04-08
> **3dmatrix said:**
> [QUOTE=vasa1;11827458]...Perhaps you could share some sample pdfs using Google Docs?

Have prob accessing Google Docs from where i live :) its 'blocked' ![/QUOTE]
You could try attaching your sample pdfs here as long as they are less than 195kB in size.  Simply use the "paperclip" icon in the forum editor screen to add your attachments.

---

### Post by Sef on 2012-04-08
> One of the best approach according to me is to install Open Office. I still use open office due to libre office issues. Libre Office is relatively newer and buggy ( it recently got out of the beta).


Libre Office is a fork of Open Office. Most of the developers who worked on Open Office quit and have been working on Libre Office instead.

---

### Post by madjr on 2012-04-08
> **3dmatrix said:**
> Yes i sent some files created with Firefox and all of them openeed at the receiving end but the one made with Liber Office did not.

Where as all of them opened in the Xp partition on my comp.

Have prob accessing Google Docs from where i live :) its 'blocked' !

maybe you should try other online alternatives like zoho docs / viewer , etc.:

[http://www.goospoos.com/2010/12/best-free-online-document-editors/](http://www.goospoos.com/2010/12/best-free-online-document-editors/)


also try **Websites To Publish & Share Your PDFs Online**

[http://www.makeuseof.com/tag/websites-to-publish-share-your-pdfs-online/](http://www.makeuseof.com/tag/websites-to-publish-share-your-pdfs-online/)

or slideshare:
[http://www.slideshare.net/](http://www.slideshare.net/)


we are in 2012 , so when sharing stuff **keeping it Online** is usually the best way. So forget about the 1997 way of doing things.

---

### Post by rmil on 2012-04-08
> **3dmatrix said:**
> Yes i sent some files created with Firefox and all of them openeed at the receiving end but the one made with Liber Office did not.

Where as all of them opened in the Xp partition on my comp.

Have prob accessing Google Docs from where i live :) its 'blocked' !

Guessing. Had similar problem in the past OO did not save pdf file until the end over the mounted CIFS network. Hence I could not open pdf file. Try saving file on Desktop.

---

### Post by 3dmatrix on 2012-04-10
Well i always save it on Desktop.

I am not able to attach that file here as it is of abt 4Mb.
But i realize now that i was foolishly thinking abt font and similar problems as there is no text in that file. Only a lot of scanned images. The images were inserted in the Liber Office doc and exported as pdf. It opened in many comp i tried but it didnt open in one of my friend's comp.

I was wondering what could have gone wrong !

---

### Post by mastablasta on 2012-04-10
you can put it on Ubuntu One and then make it public and share it.

---

### Post by 3dmatrix on 2012-04-10
> **mastablasta said:**
> you can put it on Ubuntu One and then make it public and share it.

Ok ! I never used Ubuntu One :) so first let me have a look at that !

---

