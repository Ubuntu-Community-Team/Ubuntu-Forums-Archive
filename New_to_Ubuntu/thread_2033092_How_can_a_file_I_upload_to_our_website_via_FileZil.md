---
title: "How can a file I upload to our website via FileZilla be visible in web browser?"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by hanzj on 2012-07-25
Hello, We have a website hosted by GoDaddy. It's running on Wordpress.
Using Filezilla, I uploaded one PNG file to a newly created subfolder. I gave the subfolder and the PNG file chmod permissions of 777. How come when I try to view the PNG in my Google Chrome, I'm asked for username and password?

I want the PNG to be visible to the public in a web browser.

Am I dealing with a FTP-HTTP problem?

---

### Post by mapes12 on 2012-07-25
Uploading an image file to a folder on your website will do nothing unless you have the html code in your web page(s) configured to display it in your browser. It will simply sit there on the server.

You're being asked for your username and password to access your GoDaddy web space account to authenticate you into your account to access your files. This is your protection against others messing with your web pages and supporting assets.

---

### Post by Bufeu on 2012-07-25
The password the website asks for is your password to your GoDaddy-account, not to "the server *itself*". As mapes12 said, this is the protection to prevent that other can access to your data and mess up things.

---

### Post by hanzj on 2012-07-25
Thanks, bufue and mapes.
What can i do to make the file visible to the entire world.

---

### Post by mapes12 on 2012-07-25
As I said before, you need to configure the html/css in your web page(s) to tell the web browser where and how to display the image. 

If you can share the site URL and provide some detail about where you want the image to display we can take a look at the page code. But you will still need to configure all this yourself.

BTW this has turned out to be a web page development question, not an Ubu beginners question. You may want to seek out a GoDaddy forum for this question and where I'm sure you will get access to many more developers that specialise in web hosting

Mark

---

### Post by hanzj on 2012-07-25
I'm trying to get a direct link to the PNG file stored in my hosted account.

---

### Post by mapes12 on 2012-07-25
> I'm trying to get a direct link to the PNG file stored in my hosted account.

Then you need to reference it via your site domain like this:-

[www.mysite.com/folder_name/file_name](www.mysite.com/folder_name/file_name)

This will permit people who you give the URL to the ability to download the file, but it will not display in a web browser.

---

