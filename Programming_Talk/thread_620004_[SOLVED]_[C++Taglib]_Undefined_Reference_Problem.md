---
title: "[SOLVED] [C++/Taglib] Undefined Reference Problem"
date: 2007-11-22
forum: Programming Talk
---

### Post by open_coder on 2007-11-22
I am working on some test programs using Taglib with KDE. I installed the libtag1-dev package and I have a problem.

Here is the code for my runfile:
```
// Taglib test program.

#include <taglib/id3v2tag.h>
#include <taglib/mpegfile.h>
#include <iostream>
#include <taglib/tstring.h>

using namespace std;

using namespace TagLib::MPEG;
using namespace TagLib::ID3v2;

int main(){
	
	File file("test.mp3");
	
	Tag *tag = file.ID3v2Tag();
	
	//const char *blarg = tag->artist().toCString();
	cout << tag->artist().toCString() << endl;
	//cout << tag->album() << endl;
	//cout << tag->title() << endl;
	
	return 0;
}
```

and this is the error I get when I try to run it:
```
tagtest.cpp:(.text+0xa3): undefined reference to `TagLib::MPEG::File::File(char const*, bool, TagLib::AudioProperties::ReadStyle)'
tagtest.cpp:(.text+0xb6): undefined reference to `TagLib::MPEG::File::ID3v2Tag(bool)'
tagtest.cpp:(.text+0xe8): undefined reference to `TagLib::String::toCString(bool) const'
tagtest.cpp:(.text+0x113): undefined reference to `TagLib::String::~String()'
tagtest.cpp:(.text+0x126): undefined reference to `TagLib::String::~String()'
tagtest.cpp:(.text+0x13b): undefined reference to `TagLib::MPEG::File::~File()'
tagtest.cpp:(.text+0x151): undefined reference to `TagLib::MPEG::File::~File()'
collect2: ld returned 1 exit status

```

I assume this means that the constructors I am using are declared but not defined. How is this possible, though? I am using a packaged library. 

All help appreciated. Thanks

OC

---

### Post by public_void on 2007-11-22
What is the command your using to compile? Those errors are from ld the linker. It seems as if your not linking to the correct libraries. You should have something like
```
g++ myprogam.cpp -o myprogram -ltag
```
The important part is -ltag, to inform the linker to link to libtag.

---

### Post by open_coder on 2007-11-22
Thank you. I forgot the -ltag flag. 

OC

---

### Post by tgnelson85 on 2007-12-04
Hi,

First post here.

I am having a similar problem, but using C.  I've tried using:

gcc test.c -o test -ltag

but i still get the linker errors.



Any suggestions as to why i am still getting this?


EDIT:

Managed to solve it with:
gcc test.c `taglib-config --cflags --libs` -o test -ltag_c

---

### Post by t3hi3x on 2007-12-15
i'm getting a very different problem. i have the dev packages install and i am using the same code and same compile commands.

here is what i get with g++

```
g++ ttadd.cpp -o ttadd -ltag
In file included from ttadd.cpp:3:
/usr/local/include/taglib/id3v2tag.h:25:17: error: tag.h: No such file or directory
/usr/local/include/taglib/id3v2tag.h:26:25: error: tbytevector.h: No such file or directory
/usr/local/include/taglib/id3v2tag.h:27:21: error: tstring.h: No such file or directory
/usr/local/include/taglib/id3v2tag.h:28:19: error: tlist.h: No such file or directory
/usr/local/include/taglib/id3v2tag.h:29:18: error: tmap.h: No such file or directory
In file included from ttadd.cpp:4:
/usr/local/include/taglib/mpegfile.h:25:19: error: tfile.h: No such file or directory
In file included from /usr/local/include/taglib/mpegfile.h:27,
                 from ttadd.cpp:4:
/usr/local/include/taglib/mpegproperties.h:25:29: error: audioproperties.h: No such file or directory
/usr/local/include/taglib/id3v2frame.h:61: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2frame.h:66: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:76: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:83: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:91: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:102: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:109: error: ‘String’ does not name a type
/usr/local/include/taglib/id3v2frame.h:114: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2frame.h:120: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2frame.h:132: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:160: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:167: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:173: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2frame.h:180: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2frame.h:216: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:225: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:225: error: ‘TagLib::ID3v2::Frame::Header::Header(int)’ cannot be overloaded
/usr/local/include/taglib/id3v2frame.h:216: error: with ‘TagLib::ID3v2::Frame::Header::Header(int)’
/usr/local/include/taglib/id3v2frame.h:238: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:244: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:244: error: ‘void TagLib::ID3v2::Frame::Header::setData(int)’ cannot be overloaded
/usr/local/include/taglib/id3v2frame.h:238: error: with ‘void TagLib::ID3v2::Frame::Header::setData(int)’
/usr/local/include/taglib/id3v2frame.h:250: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2frame.h:260: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2frame.h:266: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:271: error: ‘uint’ has not been declared
/usr/local/include/taglib/id3v2frame.h:277: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:287: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:295: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2frame.h:371: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2framefactory.h:63: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2framefactory.h:71: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2framefactory.h:71: error: ‘TagLib::ID3v2::Frame* TagLib::ID3v2::FrameFactory::createFrame(int) const’ cannot be overloaded
/usr/local/include/taglib/id3v2framefactory.h:63: error: with ‘TagLib::ID3v2::Frame* TagLib::ID3v2::FrameFactory::createFrame(int) const’
/usr/local/include/taglib/id3v2framefactory.h:82: error: ‘String’ has not been declared
/usr/local/include/taglib/id3v2framefactory.h:82: error: expected ‘;’ before ‘defaultTextEncoding’
/usr/local/include/taglib/id3v2framefactory.h:91: error: ‘String’ has not been declared
/usr/local/include/taglib/id3v2framefactory.h:91: error: expected ‘,’ or ‘...’ before ‘encoding’
/usr/local/include/taglib/id3v2tag.h:52: error: expected initializer before ‘<’ token
/usr/local/include/taglib/id3v2tag.h:53: error: expected initializer before ‘<’ token
/usr/local/include/taglib/id3v2tag.h:101: error: expected class-name before ‘{’ token
/usr/local/include/taglib/id3v2tag.h:132: error: ‘String’ does not name a type
/usr/local/include/taglib/id3v2tag.h:133: error: ‘String’ does not name a type
/usr/local/include/taglib/id3v2tag.h:134: error: ‘String’ does not name a type
/usr/local/include/taglib/id3v2tag.h:135: error: ‘String’ does not name a type
/usr/local/include/taglib/id3v2tag.h:136: error: ‘String’ does not name a type
/usr/local/include/taglib/id3v2tag.h:137: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2tag.h:138: error: ‘uint’ does not name a type
/usr/local/include/taglib/id3v2tag.h:140: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:141: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:142: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:143: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:144: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:145: error: ‘uint’ has not been declared
/usr/local/include/taglib/id3v2tag.h:146: error: ‘uint’ has not been declared
/usr/local/include/taglib/id3v2tag.h:205: error: expected ‘;’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:217: error: expected ‘;’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:230: error: expected ‘;’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:256: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:261: error: ‘ByteVector’ does not name a type
/usr/local/include/taglib/id3v2tag.h:276: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/id3v2tag.h:282: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/local/include/taglib/mpegproperties.h:43: error: expected class-name before ‘{’ token
/usr/local/include/taglib/mpegproperties.h:49: error: ‘ReadStyle’ has not been declared
/usr/local/include/taglib/mpegproperties.h:49: error: ‘Average’ was not declared in this scope
/usr/local/include/taglib/mpegfile.h:48: error: invalid use of undefined type ‘struct TagLib::File’
/usr/local/include/taglib/id3v2tag.h:35: error: forward declaration of ‘struct TagLib::File’
/usr/local/include/taglib/mpegfile.h:76: error: ‘class TagLib::MPEG::Properties::ReadStyle’ has not been declared
/usr/local/include/taglib/mpegfile.h:87: error: ‘class TagLib::MPEG::Properties::ReadStyle’ has not been declared
/usr/local/include/taglib/mpegfile.h:111: error: ‘Tag’ declared as a ‘virtual’ field
/usr/local/include/taglib/mpegfile.h:111: error: expected ‘;’ before ‘*’ token
/usr/local/include/taglib/mpegfile.h:254: error: ‘class TagLib::MPEG::Properties::ReadStyle’ has not been declared
/usr/local/include/taglib/mpegfile.h:76: error: ‘Average’ is not a member of ‘TagLib::MPEG::Properties’
/usr/local/include/taglib/mpegfile.h:87: error: ‘Average’ is not a member of ‘TagLib::MPEG::Properties’
ttadd.cpp: In function ‘int main()’:
ttadd.cpp:20: error: ‘class TagLib::ID3v2::Tag’ has no member named ‘artist’


```

the really weird thing is it compiles just fine in gcc with the above command.

---

### Post by t3hi3x on 2007-12-15
:shock:

well i added the `taglib-config --cflags --libs` to it and that worked.

lol

---

### Post by sruthihsr on 2011-07-28
I am having a similar problem on compiling with Qt and Fedora 9. How do i go about resolving the issue?

---

