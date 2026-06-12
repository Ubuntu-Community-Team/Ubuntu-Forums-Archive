---
title: "how to make your own format..."
date: 2007-07-30
forum: Programming Talk
---

### Post by hockey97 on 2007-07-30
Hi I want to know how to make your own file extension.

like in 3d models their are .3ds, .max .3dsmax, .obj, .mdl, ect..

well I want to know how to create your own, I know the format is nothing put how you set up the scripting layout.

but I don't know how to make your own.

I know c++ and python.

I learn though books and online tutorials of c++ and python, but never saw how formating a file is done.

and registereing it in the registry in windows. 

I know their is a website that tells how you can convert existing file extensions.

like from .zip to .rar ect the exisitng formats but I want to create my own.

and can't find any place to explain the tech area of how a file extension is made.

I know in EA games their games they make their own formats for animation and also data files and 3d models also.

do any of you know a website or could you explain how to make a format.

weather it's a data file or a 3d graphic file.

explain the differents on how to tell windows or other oprerating system if the file is a photo or a 3d model or a data file.

Thanks for your time.

---

### Post by LaRoza on 2007-07-30
Making your own format is a rather interesting goal.

The files you see are in Binary. The first 7 or 8 bytes are called the "Header", every file format has a different header. (Nobody works in binary usually, use hex)

For example, a .png file has a header of "89 50 4E 47 0D 0A 1A 0A" in hex. The file extension has nothing to do with the file, but Windows uses them, rather foolishly, to to determine what program opens it. 

Many apps look at the header, every file format has a different header, and this determines what the file is rendered as. 

I don't know if this is your goal as a format, but that is a little bit of the process.

If you want to make a format like OpenOffices, or HTML, you can make your own XML application, using XML's rules. SVG, MathML, and XHTML are all XML applications. XML is plain text, not binary, which makes it portable.

---

### Post by FuturePast on 2007-07-30
A "format" is just some data written to a file in a particular structure/order.
That's all there is to it.

---

### Post by Wybiral on 2007-07-30
A file format for storing data is just a rule by which you read and write data. Nothing special.

---

### Post by Bram001 on 2007-07-31
To find out how 'formats' work you need to find the specifications for them. Most open formats have their specifications available on the web. 
You could look up the zip format specifications and examine a file with a hex editor to learn more about it. Also you could rename an OpenDocument file to .zip and open it to see how that looks inside. All you need to learn about format is a hex-editor, an xml-editor and a bit of curiosity.

OSes tell the difference between formats because they have been implemented. Wanting them to recognize a homemade format is like inventing your own grammar and expecting other people to understand it.  EA can make their own formats because their games are the only software that needs to read the format.

---

### Post by LaRoza on 2007-07-31
Because the OP mentioned graphics and other non-text files, I mentioned binary files.

---

### Post by hockey97 on 2007-08-02
So do you think I should open that .zip file in a hex editor, and look at it, 

would by looking at it I would see a pattern??

like  how could I convert, format's.

what do you think I should to just for pratice somthing simple and quick, well, somthing that I don't have to spend a year on it, that would give me some experience and fully see how format's work for myself.

any idea's I should do, to gain experience, and get to play with it safely,meaning that I wont damage my computer if I made some error's in the script.

Thanks...!!

---

### Post by pmasiar on 2007-08-02
File format is just a "convention" - often there is no info about the format to see in the file itself. If you do not understand this, maybe you have other things to learn about using computers about which we don't know yet. :-)

maybe you can just start by reading and writing text files.

---

### Post by Wybiral on 2007-08-02
You're not going to find a pattern in a zip file (that's the point).

There is a big difference between a compression algorithm and a file format.

File formats don't always have to be binary (you mentioned 3d models, look at the wavefront ".obj" model format... It's text)

A file format is just a rule system for how the data is stored. There is no "this is how to make a file format" because it's greatly dependent on the data structure you need to store.

If you need compression, use ZLib (it's free and open)... It's used in gz's and png's and is lossless and efficient.

You can also use ZLib with your own file format to compress whatever data structure you are trying to store.

---

