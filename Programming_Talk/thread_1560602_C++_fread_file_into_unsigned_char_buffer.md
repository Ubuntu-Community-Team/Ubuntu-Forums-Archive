---
title: "C++ fread file into unsigned char buffer"
date: 2010-08-25
forum: Programming Talk
---

### Post by rabatitat on 2010-08-25
Hello all,

I'm currently suffering analysis paralysis and would like to ask your opinions on the following class. The whole thing will mostly read files with either UCS2(BE/LE) or ASCII encodings and I'm still a n00b with locales.

Should I:
a. leave it as is call fopen and malloc in the constructor and fclose and free in the destructor
b. discard the file_pointer member variable and make it local to the constructor.
c. discard the buffer and do byte by byte reading on the open file (makes it easier for fixed-width UCS2).

Regardless of the answer to the above question, should I use ifstream then convert char* from ifstream::read() to unsigned char?

Code follows.

```

/* my_file.h */
class MyFile(const char* filename)
{
    public:
        MyFile(void);
        ~MyFile(void);

    private:
        FILE* file_pointer;
        long int file_size;
        unsigned char* file_buffer;
}

/* my_file.cpp */
/* ctor */
MyFile::MyFile(const char* filename)
    : file_pointer(fopen(filename, "rb")),
    file_size(0),
    file_buffer(NULL)
{
    if (file_pointer) {
        fseek(file_pointer, 0, SEEK_END);
        file_size = ftell(file_pointer);
        rewind(file_pointer);
        file_buffer = (unsigned char*)malloc(sizeof(unsigned char) * file_size);
    }
    else
        throw std::runtime_error("File Open Error");
}

/* dtor */
MyFile::~MyFile(void)
{
    fclose(file_pointer);
    if (file_buffer != NULL)
        free(file_buffer);
}

```

Thank you in advance.

---

### Post by dwhitney67 on 2010-08-25
> **rabatitat said:**
> 
...

Should I:
a. leave it as is call fopen and malloc in the constructor and fclose and free in the destructor
b. discard the file_pointer member variable and make it local to the constructor.
c. discard the buffer and do byte by byte reading on the open file (makes it easier for fixed-width UCS2).

a. No.
b. Yes.
c. Yes.

> **rabatitat said:**
> 
Regardless of the answer to the above question, should I use ifstream then convert char* from ifstream::read() to unsigned char?

Yes, although there is no need to perform a conversion, per se.  read() will accept an unsigned char buffer as long as it is casted correctly.

Btw, you did not really indicate in your post what you have planned for the MyFile class.  So far you have it determining the size of the file, in an inefficient manner.  You would be better served using stat().  (see note below).

If your intent is to develop a wrapper-class around the fstream class, then I would suggest that the class accept an istream object, versus a const char*.  That way the class can read from various input streams (files, standard-in, etc).


Note:  stat() may not (and probably is not) available under Windoze.  If you are developing portable code for that despicable OS, then use the seekg() and tellg() fstream methods.

---

### Post by worksofcraft on 2010-08-25
I too was wondering what you had in mind for your class. If it's some potentially huge file of text data e.g. utf-8 then you should definitely do character input. Buffering is all handled transparently to you then.

OTOH if you want to read smaller binary objects like say icon images then you are not far wrong the way you are doing it now.

In that case you might want to look at the zlib package so you can save disk storage space, although personally I thought the old DOS way of having compressed drives was quite neat as you could leave storage efficiency to your file system and reap the benefits everywhere.

---

### Post by rabatitat on 2010-08-26
> **dwhitney67 said:**
> a. No.
b. Yes.
c. Yes.


Yes, although there is no need to perform a conversion, per se.  read() will accept an unsigned char buffer as long as it is casted correctly.

Btw, you did not really indicate in your post what you have planned for the MyFile class.  So far you have it determining the size of the file, in an inefficient manner.  You would be better served using stat().  (see note below).
Thanks. :D

It's supposed to read text files with varied encodings (so far it's ASCII and UCS2(BE/LE) but might have to also accept other (variable width) encodings. Data from the files are then loaded into C structs which will be passed to a C library for further processing down the line. File sizes ~5MB and would probably grow larger over time.

> **dwhitney67 said:**
> 
If your intent is to develop a wrapper-class around the fstream class, then I would suggest that the class accept an istream object, versus a const char*.  That way the class can read from various input streams (files, standard-in, etc).
No, I just want to read a file.

> **dwhitney67 said:**
> Note:  stat() may not (and probably is not) available under Windoze.  If you are developing portable code for that despicable OS, then use the seekg() and tellg() fstream methods.

Yes, it has to work on Windoze. *sigh* Then I have to "port"/compile it for .NET CLI. *groan*

---

