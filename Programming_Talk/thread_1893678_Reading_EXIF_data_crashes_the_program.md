---
title: "Reading EXIF data crashes the program"
date: 2011-12-10
forum: Programming Talk
---

### Post by hakermania on 2011-12-10
Hello all :D
I am trying to read the exif data of a list of images.
First, I sort out all the non-jpeg images and then I go inside a loop which runs this function for every image:
```

void Extras::get_exif(QString filename){
    ExifData *data;
    data = exif_data_new_from_file(filename.toLocal8Bit().data());
    ExifEntry *entry;
    ExifByteOrder byte_order;
    byte_order = exif_data_get_byte_order (data);

    /* get orientation*/
    if ((entry = exif_content_get_entry( data->ifd[EXIF_IFD_0], EXIF_TAG_ORIENTATION)))
     {
          qDebug() << "Orientation is " << exif_get_short(entry->data, byte_order);
     }
    delete data;
    delete entry;
}

```

The above code reads just fine all the images that contain EXIF data related to the orientation, like some jpeg images I had from my digital camera, but it crashes on 
```

entry = exif_content_get_entry( data->ifd[EXIF_IFD_0], EXIF_TAG_ORIENTATION)

```
if the jpeg image doesn't come from a digital camera and thus it doesn't contain the corresponding EXIF data...
The 'data->ifd[EXIF_IFD_0]' is invalid or something. I don't know.
Looking at the code of this function (exif_content_get_entry):
```

[[FONT=monospace][/FONT]ExifEntry]("http://libexif.sourceforge.net/internals/struct__ExifEntry.html")
* [exif_content_get_entry]("http://libexif.sourceforge.net/internals/exif-content_8c.html#c72bb2dacf0da27156c2c4dce08eef5d") ([ExifContent]("http://libexif.sourceforge.net/internals/struct__ExifContent.html") *content, [ExifTag]("http://libexif.sourceforge.net/internals/exif-tag_8h.html#1a0ded93d47585f6889eb546915d0f41") [tag]("http://libexif.sourceforge.net/internals/mnote-canon-tag_8c.html#f81b5c697b6608b9a512a4bf55f025e8"))
{
unsigned int i;
if (!content)
   return (NULL);
         for (i = 0; i < content->[count]("http://libexif.sourceforge.net/internals/struct__ExifContent.html#83e0ab89fd53da23fec28563450b7c02"); i++)
   if (content->[entries]("http://libexif.sourceforge.net/internals/struct__ExifContent.html#bfcd8677a7e44b7eaf5ce9c65e7a0ed0")[i]->[tag]("http://libexif.sourceforge.net/internals/struct__ExifEntry.html#a03a4dc9fa98c8bbc447c19a4d0536e9") == tag)
      return (content->[entries]("http://libexif.sourceforge.net/internals/struct__ExifContent.html#bfcd8677a7e44b7eaf5ce9c65e7a0ed0")[i]);
return (NULL);[FONT=monospace]
[/FONT]}[FONT=monospace]
[/FONT]
```
it seems that even if 'content' is invalid, it shouldn't crash.

Any help appreciated.

---

### Post by r.darwish on 2011-12-11
exif_data_new_from_file may fail and I returns NULL when it does. Since you don't preform a NULL check after you call exif_data_new_from_file, There's a possibility that "data" will be NULL.
The line:
```
entry = exif_content_get_entry( data->ifd[EXIF_IFD_0], EXIF_TAG_ORIENTATION)
```
which comes later can cause a NULL dereference, resulting a crash.

---

### Post by hakermania on 2011-12-11
> **r.darwish said:**
> exif_data_new_from_file may fail and I returns NULL when it does. Since you don't preform a NULL check after you call exif_data_new_from_file, There's a possibility that "data" will be NULL.
The line:
```
entry = exif_content_get_entry( data->ifd[EXIF_IFD_0], EXIF_TAG_ORIENTATION)
```which comes later can cause a NULL dereference, resulting a crash.

Thanks for the answer!

To my way of thinking, if(NULL) is similar to if(0), so if 'data' is NULL then 
if(entry = NULL) would be false.

Not sure why it was crashing. The problem was solved with an if(data) check but still I want to know why :/

---

### Post by ofnuts on 2011-12-11
> **hakermania said:**
> Thanks for the answer!

To my way of thinking, if(NULL) is similar to if(0), so if 'data' is NULL then 
if(entry = NULL) would be false.
If **[FONT=Courier New]data[/FONT]** is NULL then you crash trying to set **[FONT=Courier New]entry[/FONT]** by dereferencing [FONT=Courier New]**data**[/FONT].

---

### Post by hakermania on 2011-12-11
> **ofnuts said:**
> If **[FONT=Courier New]data[/FONT]** is NULL then you crash trying to set **[FONT=Courier New]entry[/FONT]** by dereferencing [FONT=Courier New]**data**[/FONT].

Oh, got it, solved.

---

