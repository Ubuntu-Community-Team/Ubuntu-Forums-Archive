---
title: "word processing software questions"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by gaitedlady on 2012-04-19
Hello,

I'm hoping someone might help me understand something, and perhaps tell me if I'm doing something wrong, if there's a solution or better software out there for my needs.  

I began to notice something odd in my text documents about a year ago after I converted my old .doc documents into Libre where I would make minor changes and then "save" the document.  These are large documents.  When I would re-open the document, there would be parts of words, sometimes just one letter missing on some words and in other times several word 'strings' would be missing.  Another issue:  I received comments back from someone that there were these spaces between my apostrophe and the letter "s" on all my possessive nouns (Jane's came out as Jane' s).  I'm thinking what the hell?  I don't type that way!

Let me add here that I am a writer.  My novels are all approx. 100K words, about 350 text pages.  Within my circle of friends we have all lamented the fact that this crap happens to all of us, making us all have to proof "one more time" (even though we've all proofed until our eyes bleed!) before hitting "send" to our editors.

So, this past weekend at lunch, twelve of us (all professional freakin' writers and not a one of us is very fluent in computer speak I might add!), are sitting in a Chinese restaurant and are debating the merits of using word processing programs (which most of us have always used,) or switching over to something like Scrivener.  Someone at the table said Scrivener doesn't have a Linux version yet, but I see where there has been some beta testing in progress.  After giving a cursory glance at several of these writing softwares, I think there's a lot of bells and whistles in them that are fluffy and unnecessary (just my opinion,) but they might be worth the money IF it fixed that stupid problem!!!!

Is there something about word processing programs that makes letters or words disappear when we have to combine 20+ chapters into one document?  (or randomly add that space between the apostrophe and the 's'?)

My engineer grad student daughter finally convinced me (out of frustration on her part, I'm sure,) to convert everything over to Linux and Ubuntu a year or so ago.  It has been amazingly intuitive to understand and learn....  except for this one thing.

Insights?  Advice?

---

### Post by sudodus on 2012-04-19
It's too bad that the converter was 'thinking' and 'correcting' instead of just converting the format from doc to odt. There are alternatives though. So if you have backup copies of the old doc files, I suggest that you try some other software, that might not do the 'thinking' and 'correcting' stuff.

- Abiword (light-weight word processor)
- LyX (a document processor)

> What is LyX?

LyX is a document preparation system. It excels at letting you create complex technical and scientific articles with mathematics, cross-references, bibliographies, indices, etc. It is very good at documents of any length in which the usual processing abilities are required: automatic sectioning and pagination, spell checking, and so forth...

You can install them with the commands
```
sudo apt-get install abiword
sudo apt-get install lyx
```

---

### Post by newbie-user on 2012-04-19
I'd recommend Google Docs, that way your document is the same regardless of what platform you're using.

---

### Post by gaitedlady on 2012-04-19
So if I install LyX do I create documents in that program to import my .doc documents into, then save that document in THAT format?  

I'm not understanding how it would work, and really appreciate any help.

---

### Post by sudodus on 2012-04-19
> **gaitedlady said:**
> So if I install LyX do I create documents in that program to import my .doc documents into, then save that document in THAT format?  

I'm not understanding how it would work, and really appreciate any help.
I recently learned about LyX, downloaded and tested it a little. But I can't help you much. Please learn about it from the built-in tutorial or from the internet (the LyX home page etc). If you are lucky, someone with experience will show up in this thread. Or ask your daughter, she might be interested ;-)

---

### Post by gaitedlady on 2012-04-19
> **newbie-user said:**
> I'd recommend Google Docs, that way your document is the same regardless of what platform you're using.

Now I have a silly question....  Do I have to be ONLINE in order to work in Google docs?  Is it a software that I download?  Also, I'm not sharing documents online, I'm writing and submitting to my agent and editor.

---

### Post by Mark Phelps on 2012-04-19
> **gaitedlady said:**
> Now I have a silly question....  Do I have to be ONLINE in order to work in Google docs?  Is it a software that I download?  Also, I'm not sharing documents online, I'm writing and submitting to my agent and editor.

As far as I've been able to find out, Google Docs uses the "cloud" concept -- which is the latest "fad" phrase for saying the files are not local to your PC.  You have to upload the docs to the Google servers first, and THEN work on them.

The big plus (that Google claims!) is that this makes your docs accessible from anywhere -- which is something you don't need if you're comfortable with having them ONLY local to your PC -- which does appear to be what you want.

Personally, I feel that Google has enough "visibility" into everything I search for; I don't need them having access to everything I write as well.

OH, and BTW, Microsoft offers much the same features with their Live version of MS Office -- upload your docs to their servers and work on them online -- which to me, suffers from the same problems.

---

### Post by souravc83 on 2012-04-19
If I maybe allowed to be old-fashioned, let me say, just use LaTex.
Open up gedit, type, and compile with LaTeX.
Or if you use a LaTeX Editing software, such as TexMaker, you can see the pdf output with one click of a mouse.

You will have complete control over what formatting you make, and where you want to save it etc.

All these fashionable editors don't make sense to me. They have all these bells and whistles, and don't do simple stupid things well enough. I don't like OpenOffice/LibreOffice at all. Google docs also has its own limitations. I wrote a novel in Google docs once. Its okay, but does limit you in certain cases. And cloud! I mean give the user the choice to save in his/her computer or the cloud.

Having said this, I must admit Word 2010 is quite good. I dunno how it works with Wine, but in a native Windows system, it is actually quite a good WYSIWYG editor. Although yes, its heavy, has problems with responding, and I am always skeptical about WYSISYG.

---

### Post by forrestcupp on 2012-04-19
If you're a writer and you heavily depend on Microsoft Word formats, then you need to be using MS Word. LibreOffice, and everything else has pretty crappy compatibility issues, especially with the newer .docx format.

All current versions of Microsoft Office can be installed to work pretty well in Linux with Wine or PlayOnLinux. I'm using Office 2007, myself. Lots of people have gotten Office 2010 to work well, too. I realize that's not an option that's free of charge, but honestly, if it's that important, it's worth spending the money on. You're not going to get perfect compatibility with anything else.

If you want to do this, have a look in the Wine subforum of the Gaming & Leisure section for some threads that talk about how to install it.

---

### Post by gaitedlady on 2012-04-19
> **forrestcupp said:**
> If you're a writer and you heavily depend on Microsoft Word formats, then you need to be using MS Word. LibreOffice, and everything else has pretty crappy compatibility issues, especially with the newer .docx format.

All current versions of Microsoft Office can be installed to work pretty well in Linux with Wine or PlayOnLinux. I'm using Office 2007, myself. Lots of people have gotten Office 2010 to work well, too. I realize that's not an option that's free of charge, but honestly, if it's that important, it's worth spending the money on. You're not going to get perfect compatibility with anything else.

If you want to do this, have a look in the Wine subforum of the Gaming & Leisure section for some threads that talk about how to install it.

I do not rely on MS at all.  Until almost two years ago, I was using it.  Daughter got frustrated that I was having other issues with computer and security on the internet, and switched me over to Linux.  I have already converted my my earlier files from .doc to .odt and what I described in the first post is the problem I am having.  I admit I love it so far, and have no desire at all to return to Windows (and I have never used a Mac.)

My friends are talking about switching over to this software call Scrivener (some people I know already have switched) but they aren't on Linux.  I don't care to switch because I won't use half the features.

I just want something that is easy for me to learn and work in, that is stable enough to keep large text documents from losing things like formatting, letters or words, and not insert spaces in odd places (like after the apostrophe and before the "s" in all my plural nouns.  I don't need it to keep track of my plot or characters.  I do that.  It's my job as the creator.

Does such a thing exist?  A simple, no-nonsense, heavy duty workhorse of a word-processor that I rely on not to do the thinking for me?

Years ago I used Word Perfect.  I started using that back in the early 80's, and used it successfully until about 2006.  What I WOULD GIVE to have that again!

---

### Post by JKyleOKC on 2012-04-20
As a professional writer who was first published nationally some 63 years ago, I'll chime in with some observations. The people who are telling you about format considerations have obviously not dealt very much with professional editors, who want simple readable copy and will turn formatting over to professional designers. And any word processor that's worthy of the name will create that simple readable copy for you.

LaTex, for instance, is a great typesetting tool and quite useful for scholarly reports. It's unbeatable for doing fancy layout, and creating beautiful arrangements of mathematical equations such as are found in doctoral dissertations. However it's totally useless for writers who depend on turning out lots of pages in a hurry to meet contract deadlines.

I used Microsoft Word starting when it ran on Windows 3.1; I did so initially because I was contributing articles to "The MS-DOS Encyclopedia" which was Microsoft's first entry into the publishing business, and they required all copy to be submitted as Word files.

I've continued to use it through the ensuing years, and use it today to do final editing on all copy for a 40-page magazine that I edit quarterly for my high school's alumni association. The reason is that our printer requires the copy to be submitted as Microsoft Publisher files, and Word is the most compatible word processor for feeding copy to Publisher.

However until that final edit time, I write the articles using AbiWord in Xubuntu. It can accept doc files as input, as well as docx (some of my contributors use recent versions of Word that create docx files; I stopped updating it with the 2000 version). AbiWord can save the documents in "rtf" format, which Word happily accepts, and there's no problem of inserting additional spaces or dropping characters or words along the way. The printed output from AbiWord is indistinguishable from that of Word, and if you save the files as "Microsoft Word" types with the ".doc" suffix, most editors will never realize that they are actually in the rtf format!

I'm suspicious of things like Scrivener; I suspect that they target the same folk who pay Venture and other vanity presses to get their work published. The purpose of a word processor is simply to replace the typewriter, for real professional writers. The true benefit is just the ease of editing, and the fact that no retyping is necessary when a chapter needs to be changed...

I hope this helps a bit!

---

### Post by gaitedlady on 2012-04-20
> **JKyleOKC said:**
> As a professional writer who was first published nationally some 63 years ago, I'll chime in with some observations. The people who are telling you about format considerations have obviously not dealt very much with professional editors, who want simple readable copy and will turn formatting over to professional designers. And any word processor that's worthy of the name will create that simple readable copy for you.

LaTex, for instance, is a great typesetting tool and quite useful for scholarly reports. It's unbeatable for doing fancy layout, and creating beautiful arrangements of mathematical equations such as are found in doctoral dissertations. However it's totally useless for writers who depend on turning out lots of pages in a hurry to meet contract deadlines.

I used Microsoft Word starting when it ran on Windows 3.1; I did so initially because I was contributing articles to "The MS-DOS Encyclopedia" which was Microsoft's first entry into the publishing business, and they required all copy to be submitted as Word files.

I've continued to use it through the ensuing years, and use it today to do final editing on all copy for a 40-page magazine that I edit quarterly for my high school's alumni association. The reason is that our printer requires the copy to be submitted as Microsoft Publisher files, and Word is the most compatible word processor for feeding copy to Publisher.

However until that final edit time, I write the articles using AbiWord in Xubuntu. It can accept doc files as input, as well as docx (some of my contributors use recent versions of Word that create docx files; I stopped updating it with the 2000 version). AbiWord can save the documents in "rtf" format, which Word happily accepts, and there's no problem of inserting additional spaces or dropping characters or words along the way. The printed output from AbiWord is indistinguishable from that of Word, and if you save the files as "Microsoft Word" types with the ".doc" suffix, most editors will never realize that they are actually in the rtf format!

I'm suspicious of things like Scrivener; I suspect that they target the same folk who pay Venture and other vanity presses to get their work published. The purpose of a word processor is simply to replace the typewriter, for real professional writers. The true benefit is just the ease of editing, and the fact that no retyping is necessary when a chapter needs to be changed...

I hope this helps a bit!

Yes, thank you!

And I agree wholeheartedly about being suspicious of a software that claims to help you write your novel.   I really just want a stable, work horse of a word processor, that allows me to save in other formats for submission, and accepts importing from other formats.  Something along the lines of the old WordPerfect.  I can't be asking for too much can I?

---

### Post by GregA on 2012-04-20
Perhaps another angle on your issues would be to check out the Libre Office forums for their advice.  There may be a default setting or property that can be changed to eliminate the problems.

[http://libreofficeforum.org/](http://libreofficeforum.org/)

---

### Post by flurospar on 2012-04-20
You might want to try Softmaker Office. I've never used it, but many people here (in my place) use it and find it to be reasonably well.

---

### Post by sudodus on 2012-04-20
> **JKyleOKC said:**
> ...
LaTex, for instance, is a great typesetting tool and quite useful for scholarly reports. It's unbeatable for doing fancy layout, and creating beautiful arrangements of mathematical equations such as are found in doctoral dissertations. However it's totally useless for writers who depend on turning out lots of pages in a hurry to meet contract deadlines.
I think LyX is similar to LaTex, but more advanced ...
> 
... However until that final edit time, I write the articles using AbiWord in Xubuntu. It can accept doc files as input, as well as docx (some of my contributors use recent versions of Word that create docx files; I stopped updating it with the 2000 version). AbiWord can save the documents in "rtf" format, which Word happily accepts, and there's no problem of inserting additional spaces or dropping characters or words along the way. The printed output from AbiWord is indistinguishable from that of Word, and if you save the files as "Microsoft Word" types with the ".doc" suffix, most editors will never realize that they are actually in the rtf format!
...
So I would again recommend AbiWord, which can be installed into any of the Ubuntu flavours and versions.

---

### Post by HermanAB on 2012-04-20
Howdy,

It sounds like you need to disable some of the 'Auto Correct' (or in this case 'auto screw-up') functions in Libre Office.

You can find them under Tools, AutoCorrect Options, Localized Options, disable 'Add non breaking space before punctuation marks' in 'French Language'.

---

### Post by kohoutek1 on 2012-04-20
> **forrestcupp said:**
> If you're a writer and you heavily depend on Microsoft Word formats, then you need to be using MS Word. LibreOffice, and everything else has pretty crappy compatibility issues, especially with the newer .docx format.

All current versions of Microsoft Office can be installed to work pretty well in Linux with Wine or PlayOnLinux. I'm using Office 2007, myself. Lots of people have gotten Office 2010 to work well, too. I realize that's not an option that's free of charge, but honestly, if it's that important, it's worth spending the money on. You're not going to get perfect compatibility with anything else.

If you want to do this, have a look in the Wine subforum of the Gaming & Leisure section for some threads that talk about how to install it.

I've been using Open/LibreOffice for years now, and I don't see major issues with compatibility. .doc works fine for me in LO. I work in editing using LO.

---

### Post by JKyleOKC on 2012-04-20
> **gaitedlady said:**
> Yes, thank you!

And I agree wholeheartedly about being suspicious of a software that claims to help you write your novel.   I really just want a stable, work horse of a word processor, that allows me to save in other formats for submission, and accepts importing from other formats.  Something along the lines of the old WordPerfect.  I can't be asking for too much can I?The best way to find out if AbiWord will handle your needs is to try it. One of the best things about using Linux is that you can try various ways to solve problems, and most of the time with no difficulty going back to previous solutions if one fails to give satisfactory results.

AbiWord is in the Software Center; all you need do to try it is to go there and click the "install" button, then give it a spin. As for import from other formats, I've not yet found one that I can't import although I'm sure a few exist. For saving in other formats, I counted 29 different ones shown as choices in the "Save As" dialog, including both doc and docx which are probably the two most widely used since Word has such a large part of the market share...

---

### Post by gaitedlady on 2012-04-21
Thank you, everyone.  It's not completely solved, but is solved-for-now.  I've downloaded AbiWrite and am playing with it this weekend.  So far, it doesn't seem too terribly different from LibreWrite, so the verdict is still out with regards to whether or not it will suit my needs.

But I still thank you all for your assistance!

---

### Post by I2k4 on 2012-04-22
I used Wordperfect professionally (legal) through the 1990s until about 2007, and know what you mean.  The major problem I've experienced, as the contributor above said, has been with _any_ type of file conversion:  regardless of fancy claims about compatibility, _no word processor program really does a good job of converting any lengthy or complex document from another program_ and that's all there is to it.  MS Word miserably bungled Wordperfect, and Open/Libre or Google Docs miserably bungle any conversion of a long or complex document from Word or anything else.  I'm not talking about letters to grandma or simple memos, but file conversion of real documents with formatted sections, chapters, tables of contents or indices. 

My impression of Libre/Open is that they are pretty sophisticated, but not many people use them yet professionally and I would not depend on writing in them and planning to convert them to Word or something else.  By comparison, Google Docs is still more like a student simple MS Works than a full featured word processor of the type a professional needs.  My main warning is, don't start using any one program with any expectation of "file compatibility" despite the smarty pants assurances from people who don't have serious word processing experience and needs. 

I'd suggest you have to get with a quality word processor that does what you want, by way of features like TOC, paragraph, header and sub-header formatting and content indexing, and then stay with it.  Also be sure it is completely compatible with what your professional readers, editors or publishers use - thankfully most modern word processing software will "print" drafts to Adobe Acrobat PDF for review and commentary and in a pinch that is a standard format that doesn't bungle up formatting.

If you're publishing to Amazon or some other ebook format, do your homework to be sure the software you are using will convert and format reliably into those proprietary files.

---

### Post by souravc83 on 2012-04-22
Microsoft formats have proprietary information, so it is hard to know how to convert. A lot of it involves guesswork and trial and error, since it is not possible to know how the formatting is coded into the document.
So, it is not surprising that .doc/.docx are not formatted well by open source word processors. How about trying lyx. You get all the advantage of LaTeX, but it is also very user friendly, so you don't have to deal with all the LaTeX compiling stuff, if that's a bottleneck.

---

### Post by sarahr on 2013-01-08
> **gaitedlady said:**
> Yes, thank you!

And I agree wholeheartedly about being suspicious of a software that claims to help you write your novel.   I really just want a stable, work horse of a word processor, that allows me to save in other formats for submission, and accepts importing from other formats.  Something along the lines of the old WordPerfect.  I can't be asking for too much can I?

As a professional and published writer, myself, I absolutely love Scrivener, particularly for the early stages of my drafts. There is currently a Linux version in beta, and free, so you may wish to try it before passing judgment so harshly. It runs under Ubuntu and variants, e.g., Linux Mint. Just be sure to follow the instructions carefully.

[http://www.literatureandlatte.com/forum/viewtopic.php?f=33&t=20489&sid=141e808afc6fc88f8c16056ff3d29fc8]("http://www.literatureandlatte.com/forum/viewtopic.php?f=33&t=20489&sid=141e808afc6fc88f8c16056ff3d29fc8")

---

