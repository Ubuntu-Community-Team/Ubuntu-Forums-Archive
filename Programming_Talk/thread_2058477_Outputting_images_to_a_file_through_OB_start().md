---
title: "Outputting images to a file through OB_start()"
date: 2012-09-15
forum: Programming Talk
---

### Post by Kurir on 2012-09-15
Hello all,

I have a small problem here. I am using the CodeIgniter framework for an application I am extending. No choice there. However one of the things I have had to add is a reporting system, which includes header images, and the ability to download these reports as files.

Outputting to a browser is fine, and outputting to a file is mostly fine, and downloading the file is fine.

I am using ob_start(), ob_get_contents() and ob_end_flush() along with fopen and fwrite to handle both outputs.

The image of course works fine in the html side of things, but when outputting to a file, something changes it so that the image, instead of referencing "insert address here" references "file:///downloaddirectory/specified address", which for obvious reasons wont work.

Is this an issue with php or is there a way around this at all? The issue happens on both windows and linux so it isnt a particular operating system causing the problem.

Thanks in advance,

Kurir

---

### Post by Ryan Dwyer on 2012-09-15
I don't get it. Are you using output buffering to create the files on the server and having the user download them with content-disposition: attachment? If so, then you need to link your images using absolute URLs (eg. [http://.](http://.).. rather than just images/whatever.png).

Why not have the user use their browser's Save Page As functionality?

---

### Post by Kurir on 2012-09-16
I am trying to make the process as easy for the un-technological as possible.

In doing so, I buffer it all, including an <img src=> tag, and then output it to a file, followed by linking to the file at the end the page with <a href>

It displays fine in the browser, but it does not display the image in the file once downloaded.

---

### Post by Ryan Dwyer on 2012-09-16
What's the exact content inside the src attribute? It must start with http:// or [https://,](https://,) otherwise it will be looking for the image on the end user's computer.

---

### Post by Kurir on 2012-09-16
> **Ryan Dwyer said:**
> What's the exact content inside the src attribute? It must start with http:// or [https://,](https://,) otherwise it will be looking for the image on the end user's computer.

Thank you so much mate, this solved my problem.

---

### Post by spjackson on 2012-09-16
If I'm reading this right, then Ryan Dwyer is right, you need to use absolute URLs.

If you write for example```
<img src="foo.jpg">
```then when this is served up by a webserver, the browser knows to get foo.jpg from the same place. However, when the same HTML file is stored locally, the browser doesn't know where it came from. In this context, "foo.jpg" simply means a file in the same local directory as the HTML file itself.

So either you need to use absolute URLs so that the images are loaded from the server, or you need to deliver the required images along with the report download. If you use absolute URLs, which solves the problem, then it is unclear what exactly the benefit is of downloading the report - you still need access to the webserver to view it properly. (There may be a benefit, such as a permanent snapshot of dynamic data that couldn't be recreated later.) If you want to deliver the images along with the HTML, then creating a zip of all the requirements seems to me the best option. Otherwise, maybe you could do the same as File->Save As via Javascript, but I don't know if this is possible and if it is whether you would need different code for each browser.

---

