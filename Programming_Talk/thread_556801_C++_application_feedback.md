---
title: "C++ application feedback"
date: 2007-09-21
forum: Programming Talk
---

### Post by dedmonds on 2007-09-21
Hello. I've been playing around with writing a simple file format conversion utility using C++ in order to push myself to learn the language (and fill some of my free time). It's not complete (lacks some error handling), but I thought it might be nice to get some feedback from someone more knowledgeable who might be willing to take a look at it and try it out. Would any of you interested in helping me out?

- Duane

---

### Post by gnusci on 2007-09-22
I would like to help you, but your question it is not good enough, it is too general. I mean, you should give better information regarding the exact problem. As your question is there must be trillions of answers out there.

* [COLOR="Red"]One way is just posting some code and some error output, it is _impossible_ for us to guess what's going wrong in your code without this minimal information.[/COLOR]

* [COLOR="Red"]Second, it is just posting what kind of file format you want to convert in to which format, in this case, you just need to post an _input/output_ example.[/COLOR]

If you provide us with more information probably you will get some answers...

---

### Post by dedmonds on 2007-09-22
Sorry. I am not aware of a problem with the program. I wondered if anyone would be willing to take a look at it and try it out in order to give me some feedback. I'm not trying to build a package that will be distributed to others. I'm just trying to learn and get better at programming in C++ on Linux. The code is meant to convert between the unix, dos, and mac line termination formats.

- Duane

---

### Post by gnusci on 2007-09-22
hummm... I think you can find several examples of such programs, anyway I have found this one:

[PHP]
#include <stdio.h>   /* Standard input/output definitions */
#include <string.h>  /* String function definitions */
#include <fcntl.h>   /* File control definitions */

int dos2unix (char *, char *);


int dos2unix(char *src_filename, char *dest_filename)
{
  FILE *in;
  FILE *out;
  int c;

  if ((in = fopen (src_filename, "r")) == NULL)
    return -1;

  if ((out = fopen (dest_filename, "w")) == NULL)
    {
      fclose (in);
      return -1;
    }

  while ((c = fgetc (in)) != EOF)
    {
        if (c != '\r')
    	{
            fputc (c, out);
	}
    }

  fclose (in);
  fclose (out);

  return 0;
}


int main(int argc, char **argv)
{
    int mainfd = 0;

    if(argc != 3)
    {
	printf("Usage: %s <in file> <out file>\n", argv[0]);
	return 1;
    }

    if(dos2unix(argv[1], argv[2]) < 0)
    {
	printf("dos2unix conversion failed, probably failed opening %s or creating temp.dat\n", argv[1]);
	return 1;

    }
    return 0;
}

[/PHP]

This is an Dos->Unix converter...

---

### Post by dedmonds on 2007-09-22
I'm not really looking for code examples. I was looking more for some feedback (tips, warnings, gotchas, etc.) on the application that I have written.

- Duane

---

### Post by aks44 on 2007-09-22
Maybe you should post a download link then?

---

### Post by dedmonds on 2007-09-22
I have attached a file to this message with what I have so far. Thanks for your help. There is a help option "cnv --help" that should display usage information.

- Duane

---

### Post by aks44 on 2007-09-22
I've quickly looked at the code, here are my thoughts at first glance:

- I don't see the point why CConverter::c_init uses text files while CConverter_Copy uses binary files. IMHO you'd be better off always using binary files. Then c_init wouldn't need to be virtual anymore, and you could move that code to the class constructor. Two step initialization is evil. If you don't want to open the files as soon as the object is constructed, maybe you should rather do something like:

```
class CConverter
{
private:
  virtual void doConversion(std::ifstream& in, std::ifstream& out) = 0;
public:
  void convert(const char* infile, const char* outfile)
  {
    std::ifstream in(...);
    std::ofstream out(...);
    // some error checking, throwing exceptions
    doConversion(in,out);
  };
};
```

No need for member i/ofstreams, nor for two-step conversion.


- Throw exceptions on errors, instead of returning error codes. Corrollary: make your code exception-safe (replace the naked pointers with some sort of smart pointer, std::auto_ptr will do fine). Just don't forget to catch the exceptions or you'll get core dumps.


- At the end of main(), no need to allocate CConverter_Copy on the heap. Using the stack will be safer, and you don't need polymorphism here anyway.


- Handling of invalid options is prone to buffer overflows. Why not just use **invalid_option(argv[1])** ??


- Argument parsing: what about **cnv <options> <input> <output> <additional args>** ? And what about an input file name that starts with a **-** ? EDIT: regarding filenames starting with **-** you may want to check eg. **rm** behaviour.


That's all for now, but I'd bet there are more problems in the arguments parsing spaghetti (no offence meant ;)).


Good luck, and keep us informed of the evolutions... :)

---

### Post by dedmonds on 2007-09-23
Thank you very much for taking a look at the code, aks44. You have given me some great feedback.

Without giving it much thought, I assumed that I needed to open the file as a text file to perform the format conversions. However, I also assumed that things would execute faster in the copy case if the file was opened as a binary file. If there is no reason not to open the file as binary in all cases, c_init has only one form. This would simplify things quite a bit. I'll look at that more closely.

I agree with you about the two-step initialization. I read the filename(s) in from the end of argument list, and I was hesitant (for some reason) to store the conversion type as a variable until I got to the filename(s) and then pass them in as arguments to the CConverter constructor. I don't think my logic made sense. It's cleaner the other way.

It never crossed my mind not to have member i/ofstreams, and I'll take a look at the std::auto_ptr template class. Also, I tend to return error codes, rather than throw exceptions in general. It's a habit I'm going to have to break.

I don't want to force an input filename convention. I am actually using this utility at work a little now, and I have no control over the filenames (short of renaming the file before and after the conversion).

I'll look closer at your suggestions and make changes to the code. I really appreciate you taking the time to go through the code. It really goes a long way in helping me get better at this. I would like to get to the point that I could contribute to an open source project in a meaningful way.

- Duane

---

### Post by dwhitney67 on 2007-09-23
What 'gnusci' was trying to convey to you is that they are several apps already out there that do what you want.  If you are merely wanting to exercise your brain cells into learning C++, then that is great.  If you are trying to support something (at work), then consider the following apps in /usr/bin:

[LIST]
[*]unix2dos
[*]dos2unix
[*]mac2unix
[/LIST]

There are man-page descriptions for each of the commands above.

---

