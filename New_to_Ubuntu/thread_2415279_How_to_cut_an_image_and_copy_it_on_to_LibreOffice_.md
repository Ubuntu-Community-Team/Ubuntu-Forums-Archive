---
title: "How to cut an image and copy it on to LibreOffice in Ubuntu 18.04"
date: 2019-03-23
forum: New to Ubuntu
---

### Post by zak100 on 2019-03-23
Hi,
I am trying to cut an image in Ubuntu 18.04. When I double click an image it loads it into image viewer. But I can't find cut option. Then I opened the image in shotwell Viewer. I found the "crop" option in "Photo" menu  but it is not flexible like windows paint. I can't create a square. Some body please guide.


Zulfi.

---

### Post by pardeep.saini on 2019-03-23
Hi zak100, I think you should use GIMP for image editing, it is better than windows paint.
You can install it from Ubuntu Software Center if you have not already installed it.

---

### Post by Dennis N on 2019-03-23
To copy an image into a LibreOffice writer document (as your title suggests), I just use the file manager to copy the image file, then in LibreOffice: Edit > Paste.
If you want to crop it, do that first (I use Gimp crop tool), save the cropped image, then copy that file into LibreOffice. You can resize or adjust it after pasting into L.O. too.

---

### Post by hannuke on 2019-03-24
I think Gimp is too complicated. Download gThumb. It can cut an image of the right size and adjust it in several ways. It's a good and easy program for image processing.

---

### Post by yetimon_64 on 2019-03-24
For simply cropping a square image I would tend to use the tools provided in gthumb (available in the repositories, I don't think it is standard on an install nowadays). It has about 10 or 12 aspect ratio templates that can be applied to the crop tool, which makes it a bit easier and quicker than gimp.

You don't even need to save the cropped square as a file with gthumb, I just checked by cropping a bit of an image to a square selection then right clicking and choosing copy and I was able to open libreoffice writer and paste the square image into a LO document again by using right click and selecting paste. With the aspect ratio templates in gthumb and the context menus in both gthumb and LO there is actually no need to save the cropped square selection as a separate image. 

I just tested the square selection and context menu copy in gimp that I describe above with gthumb, then pasting to a LO writer document and it works fine without needing to save to a file as well. Simply copy a selection (square) in gimp, without even cropping the image, and paste to LO.

I find the advantage is with gthumb as it supplies aspect ratio templates which makes it a bit quicker to use here; both applications have context menus and can copy/paste directly to LO easily. 

As Dennis N notes once the image selection is pasted into LO it can easily be resized to suit your document.

I use both gthumb and gimp OP, but tend to keep gimp for my more advanced editing needs that gthumb doesn't have the capabilities to do. I find gthumb quicker/easier in simple crop operations than gimp. Once a image portion is selected both can easily copy/paste directly to LO or any other application.

Regards, yeti.

---

### Post by Holger_Gehrke on 2019-03-24
And to confuse you with one more option: just insert the full image into your LibreOffice document and crop it in LibreOffice. I know that both Writer and Calc have that capability, haven't tried impress, Draw and Base, but i assume they can do it. Since it saves the full image in your document, you can change the way it is cut at any time. The big drawback with this approach is the size of the resulting file; if you have several small pieces of very big images in your Document, you'll end up with a file much bigger than expected.

Holger

---

### Post by zak100 on 2019-03-24
Hi,
I tried by pressingboth PrtSc and Shift-PrtScr. I heard the camera's clicking in both cases. But when I pressed "paste" option in Libre Office, I did not get anything.

Zulfi.

---

### Post by hannuke on 2019-03-24
Go to Folders -> Images -> Find Image and right-click and select copy.

---

