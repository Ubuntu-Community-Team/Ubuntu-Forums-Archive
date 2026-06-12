---
title: "Displaying an image to a window and then clearing it"
date: 2011-08-10
forum: Programming Talk
---

### Post by Atirag on 2011-08-10
Hello I have been making a program to display an image on a window and then if people want to open another image I want the last image automatically cleared and the new one loaded

This is the code I have

```
gtk_image_clear(image);
//gtk_widget_destroy(image);

image = gtk_image_new_from_file(file);

gtk_box_pack_end(box,image,FALSE,FALSE,1);

gtk_widget_show_all(window);
```Everytime someone wants to open an image this code is run but the first line of this code crashes the program the first time since there's no image yet. 

How can I do to clear the image from the window before a new one is loaded without having this problem?

Thx for any help.

---

### Post by Bachstelze on 2011-08-10
What do you want to clear if there's no image?

---

### Post by Atirag on 2011-08-10
The first time there's no image but after you open the first image then there's always an image. If I don't clear the image before opening the new one then both images show on the window.

---

### Post by Bachstelze on 2011-08-10
Okay, so you should initialise image to a sensible value, then do something like:

```
if (image != VALUE) {
    gtk_image_clear(image);
}
```

Can you find out what that value would be?

---

### Post by Atirag on 2011-08-10
I was trying using this 

```
if(gtk_image_get_storage_type(image) != GTK_IMAGE_EMPTY)
  gtk_image_clear(image);
```But it crashes the same when trying to use gtk_image_get_storage_type

Likewise I tried this 

```
if(image != NULL)
  gtk_image_clear(image);
```but image is never NULL so I don't know what image is supposed to be

---

### Post by Atirag on 2011-08-10
Ok, initializing the image as NULL and then doing the evaluation did the trick!

```
GtkImage *image = NULL;

if(image != NULL)   gtk_image_clear(image);
```
Thx a lot Bachstelze! :)

---

### Post by Bachstelze on 2011-08-10
> **Atirag said:**
> 
```
if(image != NULL)
  gtk_image_clear(image);
```but image is never NULL so I don't know what image is supposed to be

I don't know much about GTK, but I think GTK_IMAGE_EMPTY would be a good initial value to use. You will need to find out in which cases gtk_image_new_from_file() returns GTK_IMAGE_EMPTY, and deal with them separately if necessary.

*EDIT:* Or if you can use pointers, NULL would work too. ;)

---

