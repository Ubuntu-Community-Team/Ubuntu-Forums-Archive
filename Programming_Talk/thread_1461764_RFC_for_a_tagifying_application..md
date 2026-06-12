---
title: "RFC for a tagifying application."
date: 2010-04-24
forum: Programming Talk
---

### Post by sheperson on 2010-04-24
Hi,
I don't know if this forum is the right place to post this, so forgive me if I am wrong.

I am thinking about an application for managing and performing search in my files.
Some features:
- Add tag for files, for example a photo taken by the Zriwar lake would have the tags Zriwar, Mariwan, name of persons in the photo and so on.
- Add information specific to to a file type, for example for a PDF book, it could be author, publisher, year published and so on.
- Preview support for Images, Videos and some other file types.
- Support for different file types, not only one specific one like books, photos or others.
- A good search capability.
- Multi platform!

I have seen some similar ones, but each one lacks one of the above options, for example Mendeley is good, but only for PDF files, and Calibre is for books.

Is there any such application (or similar)? If not, well I will start developing it!
Any ideas, suggestions or comments are appreciated.

---

### Post by soltanis on 2010-04-24
Hmmm. Such as JPEG tags for images, ID3 tags in MP3, and Vorbis comment tags for ogg?

I suggest you look into Mutagen -- it is an audio-tagging library compatible with many different formats.

Sounds like a good idea, if you can bring a better way to organize people's media in an intuitive way. Make it better than Apple stuff and I'll love you forever.

---

### Post by slavik on 2010-04-24
fspot + mutagen?

---

### Post by sheperson on 2010-04-25
Hi,
Thanks for your posts.
However as I said before, I want this application to be able to handle many files, and in addition to MP3 tags and Jpeg tags, it should be able to add user tags, for identifying the file, for example the book The Art of Unix Programming by Eric S. Raymond would have these tags: Unix, Programming, C++, Addison-Wesley, Year (2003) and so on.

Then the user can perform searches on the application database, which contains all the file specific tags, user defined tags and other info such as file size, file type, path to file and so on.

And for the programming, I am thinking of Qt with SQLite as the back end DB.

Besides any suggestions for the application name?
Thanks again.
:popcorn:

---

### Post by slavik on 2010-04-25
> **sheperson said:**
> Hi,
Thanks for your posts.
However as I said before, I want this application to be able to handle many files, and in addition to MP3 tags and Jpeg tags, it should be able to add user tags, for identifying the file, for example the book The Art of Unix Programming by Eric S. Raymond would have these tags: Unix, Programming, C++, Addison-Wesley, Year (2003) and so on.

Then the user can perform searches on the application database, which contains all the file specific tags, user defined tags and other info such as file size, file type, path to file and so on.

And for the programming, I am thinking of Qt with SQLite as the back end DB.

Besides any suggestions for the application name?
Thanks again.
:popcorn:
you'll have to build your own. here's a question though ... what about formats that don't support tags/information? (for example plaintext files).

---

### Post by sheperson on 2010-04-25
> **slavik said:**
> you'll have to build your own. here's a question though ... what about formats that don't support tags/information? (for example plaintext files).

Yes, I will start building one.

And if a file supports tags, then we'll use it, and if it dose not I will store the tags in the database, along other attributes which need to be stored there.

What's your idea? :KS

---

### Post by slavik on 2010-04-25
I don't have one. :P

But what will you do with things like MP3s? Where will you store tags/info for those?

---

