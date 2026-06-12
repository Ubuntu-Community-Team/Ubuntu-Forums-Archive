---
title: "Text in OpenGL - Cross Platform"
date: 2009-09-27
forum: Programming Talk
---

### Post by socool274 on 2009-09-27
I'm looking for an easy way to draw text in an OpenGL render. It has to be cross platform. More specifically, I'm looking for mac and linux, not windows, because windows already has a way to draw text. If it works for windows, too, then that's great, but it's not needed. I also need a way to load images, from any kind of format (.png, .jpg, .gif). I honestly don't have a preference of which i should be able to load. If it can load multiple formats, that's great, but not needed. The text need not be 3d rotatable, but if it is, again, that is great, but not needed. I do need the image loading to be 3d rotatable, and scalable. Thanks in advance for any help.

---

### Post by HavocXphere on 2009-09-27
OpenGL sound like a heavy overkill for drawing a bit of text to be honest.:confused:

The actual OGL code is usually cross-platform. The tricky part is the initialization of the OGL interface i.e. Creating the drawing surface. That part you'll have to code separately for each platform since it is different.

Image loading you'll probably also have to do separately for each platform since the paths etc are different. Anything to interacts with the underlying environment will have to be customized per environment. (Images, Window initialization, Sleep, Input)

The best approach is to separate the bits & pieces that need to be custom written from the rest.

i.e. Write a function called LoadImage & use that everywhere. Then you've got one central place where you can redirect the program flow depending on the platform you're writing for.

BMP is usually easiest, then png.

The main loop you'll probably have to write separately for each platform.

And finally, you mention that it must be 3D rotatable. Text is not inherently 3D and neither are images...so you'll either need to calculate the 3rd dimension on the fly or load a model. There should be 3D text modules available for any major programming language. Image rotating will be either very easy or very difficult depending on which way its rotating. If its just rotating while you still view it from the front then the easiest is to just rotate the viewpoint/camera instead of recalculating the rectangle.

EDIT: nvm, I see the text doesn't need to rotate. The rotating the view point thing only works if there is nothing else being rendered naturally.

---

### Post by socool274 on 2009-09-27
I was hoping for an already made LoadImage type function, but yes, if there wasn't one already made, then I would have to make it myself. I don't know the .bmp format, or the .png format... How is it written, if I know that, then I could make a function to load it. Also, it is in binary, which, as I understand, uses special characters. How would I read from a file, and determine which special character? From what you are saying, I'm assuming that I should create an OpenGL renderable object from LoadImage.

---

### Post by DougB1958 on 2009-09-27
I haven't looked closely at text or images in OpenGL, but I'm pretty sure that OpenGL per se doesn't really support either. I've written a little bit of code for loading raw images for use as textures, and for saving screen images produced by OpenGL in a couple of image file formats, but that's the closes I've come to what you're doing. I also seem to remember some image-processing type functions associated with textures, but I believe they leave it to you to load the texture/image you want to apply them to.

For loading images, I'd suggest you google the image format(s) you want to work with. Most of the popular ones seems to have free libraries that make loading and saving images fairly straightforward, and you may well find sample code that you could adapt for loading images into your program.

You might look into GLUT for cross-platform text. It's a cross-platform windowing toolkit for OpenGL; it's minimal in many respects, but does have some minor support for drawing text. No support for text that's represented in a way that would lend itself to 3D rotations though, so it might be too simple for your needs.

---

### Post by socool274 on 2009-09-27
I have learned GLUT, and have used it before for text, but it is too simple.

---

### Post by grayrainbow on 2009-09-28
You can try Qt, it has good(and well documented widgets for OpenGL). Do the image part first and than simply use images for text :)

---

