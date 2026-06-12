---
title: "How to use Rapidshare Downloader (RDown) Firefox add-on without updating Firefox"
date: 2008-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by TuxIsCute on 2008-08-22
[B][CENTER]How to use Rapidshare Downloader (RDown) Firefox add-on
without updating Ubuntu's Firefox default build.[/CENTER][/B]

**Introduction:**

RDown allows one to automatically download massive lists from Rapidshare one file at a time while the computer isn't being used (or even if it is) in the background without disturbing anyone.  I have been trying to get this to work for me for some time now.  Originally, I was simply going to update Firefox.  However, after following the tutorials word-for-word, I still could not get it Firefox to update.  I even tried the automated script which promptly errors-out.  So I abandoned my attempts to update Firefox.  I put everything back the way it was in the original install and set out to get the add-on I needed to work with my rouge copy of Firefox.  I am now posting my success just in case someone else out there wants to know what I did in hopes of joining me in that success.  If this helps just one person, it will be worth it, I think.

**Things you will need:**
[LIST]
[*]Ubuntu's install of Firefox (currently 3.0B5)
[*]Access to the internet (your reading this now, so good)
[*]An understanding of how to add add-ons.
[*]The ability to follow directions.
[/LIST]
[B]
The How To:[/B]

First of all, you need to go the the add-on site for Firefox and install the Rdown add-on ([https://addons.mozilla.org/en-US/firefox/addon/8376](https://addons.mozilla.org/en-US/firefox/addon/8376)).  You'll NOT be able to install the newest version so click the link which says “See all versions” and install the one that is recommended for 3.0B5 (Rdown version 0.5.3).  (NOTE: You'll need to log in to install the experimental add-ons so either just login or create a new account if you don't have one.  I'll assume you already know how to do that so...)  Don't worry, it'll work just fine.  It just doesn't have the newest bells and whistles (also take note of the freezing bug issue which hasn't been solved in this version.  I haven't run into it yet.  Once that is installed and Firefox opens back up, we are ready for the next add-on we need to download.

This next on is a bit tricky.  You'll need to go to the page for MIME Edit found at: [https://addons.mozilla.org/en-US/firefox/addon/4498](https://addons.mozilla.org/en-US/firefox/addon/4498).

You'll not be able to install this add-on because it isn't made for Firefox 3.0 (as of this writing).  What you'll need to do is (if you are still logged in—which you should still be—click the link that says “Ignore version check” which will activate the install button.  Do NOT click it as Firefox will NOT install it automatically.  We have to fix that so right click the button and select “Save link as” and save the file to your computers HDD.  You'll get (as of this writing) “mime_edit-0.60-fx+tb.xpi.”  This is basically a compressed file.  Open it in Archive Manager.  We need to extract only one file from this archive.  That is the file named “install.rdf.”  Open this file in text editor and find the line which reads: “<em:maxVersion>2.0.*.*</em:maxVersion>” and edit the 2.0.* to read 3.0.1.  Then add the file back into the archive replacing the old one.  Then open this new file in Firefox which will promptly ask you to install the add-on.  (NOTE: Doing this will cause SOME parts of the add-on not to function properly and I would not do this normally but this add-on helps us a lot so do this and remove the faulty add-on when you are done.  There is no danger in messing up Firefox or anything doing this so don't worry.)

Now that we have these two add-ons installed we can get to work making them work.  Open Firefox and go to Tools &#8594; MIME Edit.  This will open the MIME Edit add-on.  Click on the “Edit” tab to open the area we need to access.  The list of MIME's is a functionality loss (what I was talking about earlier).  Click the “New Type” button.  On this screen fill out the information as follows:

MIME Type:  application/x-rar-compressed
Description:  RAR Compression File
Extension:  rar

Select the “Save to disk” option.

Click okay.  Don't worry that nothing shows up, it did what we needed it to do.  Now click okay and notice that doesn't work.  Close this dialog by clicking the “X” in the top corner.

All of this adds the RAR MIME to Firefox.  It tells Firefox to always save RAR files to the disk without asking you for what to do with them.  (if you are downloading mass amounts of other files you can do this with the correct MIME type—search for it on Google—to allow Firefox to save that file type to disk automatically too.  However the common Rapidshare files are RARs.)

You can also add the MIME type manually by editing mimeType.rdf it resides at /home/isr/.mozilla/firefox/9u3edx35.default.  You need to make it look like this (additions in bold):

```
<?xml version="1.0"?>
<RDF:RDF xmlns:NC="http://home.netscape.com/NC-rdf#"
         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <RDF:Description RDF:about="urn:scheme:mailto"
                   NC:value="mailto">
    <NC:handlerProp RDF:resource="urn:scheme:handler:mailto"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:handler:web:http://compose.mail.yahoo.com/?To=%s"
                   NC:prettyName="Yahoo! Mail"
                   NC:uriTemplate="http://compose.mail.yahoo.com/?To=%s" />
  <RDF:Description RDF:about="urn:scheme:handler:mailto"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="false">
    <NC:possibleApplication RDF:resource="urn:handler:web:http://compose.mail.yahoo.com/?To=%s"/>
  </RDF:Description>
  <RDF:Seq RDF:about="urn:mimetypes:root">
    **<RDF:li RDF:resource="urn:mimetype:application/x-rar-compressed"/>**
  </RDF:Seq>
  <RDF:Description RDF:about="urn:schemes">
    <NC:Protocol-Schemes RDF:resource="urn:schemes:root"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:webcal"
                   NC:value="webcal">
    <NC:handlerProp RDF:resource="urn:scheme:handler:webcal"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:handler:webcal"
                   NC:useSystemDefault="true"
                   NC:alwaysAsk="true">
    <NC:possibleApplication RDF:resource="urn:handler:web:http://30boxes.com/external/widget?refer=ff&amp;url=%s"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetypes">
    <NC:MIME-types RDF:resource="urn:mimetypes:root"/>
  </RDF:Description>
  <RDF:Seq RDF:about="urn:schemes:root">
    <RDF:li RDF:resource="urn:scheme:mailto"/>
    <RDF:li RDF:resource="urn:scheme:webcal"/>
  </RDF:Seq>
  [B]<RDF:Description RDF:about="urn:mimetype:externalApplication:application/x-rar-compressed"
                   NC:prettyName="" />
  <RDF:Description RDF:about="urn:root"
                   NC:en-US_defaultHandlersVersion="1" />
  <RDF:Description RDF:about="urn:mimetype:application/x-rar-compressed"
                   NC:value="application/x-rar-compressed"
                   NC:editable="true"
                   NC:description="RAR Compression File"
                   NC:fileExtensions="rar">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/x-rar-compressed"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:application/x-rar-compressed"
                   NC:saveToDisk="true"
                   NC:alwaysAsk="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/x-rar-compressed"/>
  </RDF:Description>[/B]
  <RDF:Description RDF:about="urn:handler:web:http://30boxes.com/external/widget?refer=ff&amp;url=%s"
                   NC:prettyName="30 Boxes"
                   NC:uriTemplate="http://30boxes.com/external/widget?refer=ff&amp;url=%s" />
</RDF:RDF>
```

I've done it both ways (for this tutorial) and they both work.  This also assumes that the mimeTypes.rdf file has NOT already been edited.  If it has, yours might look different to mine.

Now you can use RDown to download a massive list of RARs from Rapidshare without having to tell Ubuntu's default Firefox to save the RAR everytime.  You can find RDown in Firefox under Tools.  Open RDown, paste in your links and press start.  It even waits for the free timer to expire.

Congratulations on getting it to work!

---

### Post by Tiftof on 2008-08-22
I just use downthemall extension for this and other downloading needs. No hassle, just installing the addon and download away!

---

### Post by aldeby on 2008-08-23
The extension has been updated recently to version 0.5.5 which is supposed to be compatible with firefox 3.0.x

However, I didn't suceed in installing it since it prompts me with a hash fail.

I have had a further search on Google and I found another very handy program:

Jdownloader [http://jdownloader.org/home_features]("http://jdownloader.org/home_features")

It's a Java based program, thus 100% compatible with Linux.

---

### Post by binbash on 2008-08-24
> **aldeby said:**
> The extension has been updated recently to version 0.5.5 which is supposed to be compatible with firefox 3.0.x

However, I didn't suceed in installing it since it prompts me with a hash fail.

I have had a further search on Google and I found another very handy program:

Jdownloader [http://jdownloader.org/home_features]("http://jdownloader.org/home_features")

It's a Java based program, thus 100% compatible with Linux.

i am using it over 2 months.Jdownloader is being developed very actively and it is quite perfect for downloading from free or premium hosts, you dont have remember passwords, extract.There is also a remote control plugin : )

---

### Post by TuxIsCute on 2008-08-26
Yes, I know it has been updated.  You should read next time, I include this bit of information right in the tutorial.  You fail at having the tools to use this tutorial, namely, the last one.

---

