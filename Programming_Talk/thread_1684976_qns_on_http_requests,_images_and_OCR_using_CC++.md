---
title: "qns on http requests, images and OCR using C/C++"
date: 2011-02-09
forum: Programming Talk
---

### Post by guest_user on 2011-02-09
hi, am doing a project which requires me to GET images using http protocol and then perform optical character recognition(OCR) on it.
Q1) Are images normally encoded using some form of encoding like Base64, etc such that I have to decode it before processing?
Q2) If so, what forms of encoding are normally used?
Q3) How do I store the received bytes, what data structure can I use, etc?
Q4) Are there any good books/references on OCR algorithms?

---

### Post by Zugzwang on 2011-02-10
Dear OP, 

is there any particular reason why you want to reinvent the wheel? If you want to get images from a HTTP server, that's fine - use a library having the required functionality, for example libcurl. If you really want to do it the hardware, read some basic network book that covers HTTP.

The same goes for OCR - Wouldn't it suffice to run some open-source OCR tool over the image and just collect the output?

---

### Post by guest_user on 2011-02-10
> **Zugzwang said:**
> Dear OP, 

is there any particular reason why you want to reinvent the wheel? If you want to get images from a HTTP server, that's fine - use a library having the required functionality, for example libcurl. If you really want to do it the hardware, read some basic network book that covers HTTP.

The same goes for OCR - Wouldn't it suffice to run some open-source OCR tool over the image and just collect the output?

Its a school project so I can't use libraries

---

### Post by Zugzwang on 2011-02-11
> **guest_user said:**
> Its a school project so I can't use libraries

Are you sure? I'm asking because implementing OCR algorithms doesn't look like something you could do in a couple of days or even weeks.

---

### Post by worksofcraft on 2011-02-11
> **guest_user said:**
> hi, am doing a project which requires me to GET images using http protocol and then perform optical character recognition(OCR) on it.
Q1) Are images normally encoded using some form of encoding like Base64, etc such that I have to decode it before processing?
Q2) If so, what forms of encoding are normally used?
Q3) How do I store the received bytes, what data structure can I use, etc?
Q4) Are there any good books/references on OCR algorithms?

The images are mostly transferred as jpeg or png and these require considerable decoding to decompress into actual pixel data that you can use.

Besides that you would have to know the image file names and paths that you want on the server and that would mean interpreting the HTML which is not trivial.

Your best bet would be to select the area on screen and extract  the pixels you want that way.

Now OCR is far from easy because characters can all be different fonts and sizes and different styles too. It is not the sort of thing that can be done as a school project IMO.

---

### Post by guest_user on 2011-02-13
> **Zugzwang said:**
> Are you sure? I'm asking because implementing OCR algorithms doesn't look like something you could do in a couple of days or even weeks.

Its a final year project...

---

### Post by Zugzwang on 2011-02-13
> **guest_user said:**
> Its a final year project...

If you really want to do it the hard way, i.e., implementing all of the following steps yourself
[LIST]
[*]Using HTTP to obtain image files
[*]Decoding PNG and/or JPG image files
[*]Making OCR on it
[/LIST]
then you are well-advised by getting books on these subjects. But please check with your advisor whether this is really necessary. Especially the second step, as worksofcraft pointed out, might be a lot of work, and if the aim of the project is to do OCR, also seems to be an unnecessary hassle.

Now to the books. The first stuff in the list is probably well-covered by the Tanenbaum standard book on networks. It should cover HTTP in enough detail to get you started.

For the rest, you can probably start by browsing your local university library.

---

