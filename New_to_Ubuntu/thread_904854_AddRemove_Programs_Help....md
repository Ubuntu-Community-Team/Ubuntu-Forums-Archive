---
title: "Add/Remove Programs Help..."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by sillyboy on 2008-08-29
:confused:I need to know which ADD program is the easiest to use.  By easy, I mean that the program WILL find what I am looking for.  I have tried to use the ADD/REMOVE under Applications, but it never finds anything.  For example, I was looking for X-n-View.  I know it will run on Linux, their website says so.

Thanks

---

### Post by SunnyRabbiera on 2008-08-29
Well for a more advanced package manger there is synaptic located under system> administration> synaptic

Synaptic works a bit like add/remove.
But also put into consideration that because an app says it has linux support doesnt mean it will be available to you right away.

---

### Post by kk0sse54 on 2008-08-29
Like the other poster said use Synaptic in order to find more packages but just because a website says that their software works under Linux doesn't mean it's in the Ubuntu repos and instead you might have download the packages and install it through a different means than apt-get

---

### Post by hopkinsjeni on 2008-08-29
> **sillyboy said:**
> :confused:I need to know which ADD program is the easiest to use.  By easy, I mean that the program WILL find what I am looking for.  I have tried to use the ADD/REMOVE under Applications, but it never finds anything.  For example, I was looking for X-n-View.  I know it will run on Linux, their website says so.

Thanks
The Add/Remove list only has programs from 2nd parties, for 3rd party programs such as X-n-View you can usually find the install instructions on the website and use your terminal to install them. I don't think there's a 'list' of such for all 3rd party programs but if you need something for a specific function the various forums usually have lots of helpful hints and recommendations.
In your terminal to add a program type
sudo apt-get install *program name*

---

### Post by SunnyRabbiera on 2008-08-29
From the looks of it though it looks like this application... kind of sucks in linux as I was able to install it.
What features is this thing supposed to have anyway?
Perhaps we can give you a valid linux alternative.

---

### Post by sillyboy on 2008-08-29
Here is the X-n-View website below.  Quite a versatile little program.
[www.xnview.com](www.xnview.com)  Let me know if there is something as good.

Thanks

---

### Post by SunnyRabbiera on 2008-08-29
> **sillyboy said:**
> Here is the X-n-View website below.  Quite a versatile little program.
[www.xnview.com](www.xnview.com)  Let me know if there is something as good.

Thanks

Yes I did look it over, doesnt seem that special to me...
What feature in it do you find most important in it?
Already I think of a few alternatives to this app but I need to know what you find of value in this app so I can suggest an alternative.

---

### Post by sillyboy on 2008-08-29
Ease of use, multi covert, over 400 extensions recognized, Very small, I'm used to using it.:)

---

### Post by sillyboy on 2008-08-29
[http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml)

Above is a website that gives more info about X-n-View.:)[http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/XnView-4612.shtml)

---

### Post by lovinglinux on 2008-08-29
I'm familiar with XnView. Have use it for many years.

Do you use XnView for organizing your media into categories, independent of the folders they are saved?

Do you use XnView for editing and batch conversions?

Or do you use XnView basically for browsing media and previewing them?

Do you use it more for videos or images?

While I do agree that is an easy to use software with great support for many different formats, I never thought it was an essential tool in my system. Anyways, maybe I can help you find an alternative or to install it if you are really going to miss it.

---

### Post by sillyboy on 2008-08-29
I use it mostly for batch conversions for sizing, naming pics.

---

### Post by SunnyRabbiera on 2008-08-29
> **sillyboy said:**
> I use it mostly for batch conversions for sizing, naming pics.

well it does seem to work in wine so if you need it that bad you can get it running that way.
Wine is how you run most windows apps under linux to install it use synaptic package manager.

---

### Post by lovinglinux on 2008-08-29
> **sillyboy said:**
> I use it mostly for batch conversions for sizing, naming pics.

For naming pics you can use pyRenamer. It is on the repositories, so you install using the Add/Remove manager.

It is a very powerful renamer. At first glance it looks complicated, but it isn't. It is just powerful. I've just learned how to use it.

For example, consider that you have a lot of jpg images that you downloaded from the net and saved in one folder, but they all have weird names. So, open pyRenamer and browser that folder. Then select all images you want to rename. Then select the "images" tab in the bottom panel.

We have two input fields to configure. If you put the mouse over the text fields, a tool tip will pop up with available expressions options that you can use.

In the first you can type {X}, so the program will replace any character (letters, numbers and spaces). In the second field type {num}.jpg. Then hit the preview button. All images will be numbered in sequence, followed by the jpg extension. 

If you have images with EXIF data you can use this embedded information to rename the files. For example, you can organize the images grouping them by resolution. Type "{imagewidth}x{imageheight}-{num3}.jpg" this will rename the files using their resolution, followed by a sequential number with 3 digits, like "1024x768-001.jpg", "1024x768-002.jpg", "1024x768-003.jpg" and so on.

As you can see, the combinations are practically unlimited and the preview button will help you to determine which is the best expression for each case.

I will try to find a batch converter now.

EDIT: your default Ubuntu installation comes with gThumb application, which can be used for batch conversions. It is not powerful as XnView, but it is simple to use and should be enough for simple conversions.

---

### Post by Cheesehead on 2008-08-29
I've had great success with Imagemagick, espcially Imagemagick + scripts once you get comfortable with the command line.

---

### Post by lovinglinux on 2008-08-29
Now talking about batch conversions.

There is an application called "Phatch Photo Batch Processor" in the repositories, so you can easily install it. It is very powerful and should do what you do with XnView (maybe even better).

The first thing different is the way you perform the conversions. In XnView and most Windows applications you select the images you want to convert, then you configure the output rules, then you convert them. With "Phatch" you first create the output rules, then you drag&drop the files you want to convert to the "Phatch" application window or open them like you usually do with any program.

This application has the advantage that you can save the output rules, so you can reuse them as you wish.

There is a tutorial at [http://photobatch.wikidot.com/getting-started](http://photobatch.wikidot.com/getting-started)

I didn't tested the quality of the output or format compatibility, but I do recommend this software due to easy of use, flexibility, output options and ability to save rules.

I'm a professional photographer and I can spot a clever application when I see one.

---

