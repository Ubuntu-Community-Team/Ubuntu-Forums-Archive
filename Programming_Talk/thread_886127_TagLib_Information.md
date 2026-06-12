---
title: "TagLib Information"
date: 2008-08-10
forum: Programming Talk
---

### Post by Neon612 on 2008-08-10
After looking for help with ID3lib and deciding against using it, I was pointed in the direction of TagLib. I've read the tutorials on their site but it doesn't go into depth on what is what. Are there any other tutorials on their library or can someone here provide a bit of help? Examples. Docs. Something.

I'm trying to get to the title, artist, album, playtime, filesize, and filename tags of the mp3's. And its in c++.

---

### Post by StOoZ on 2008-08-11
actually these simple things are mentioned in the docs  , if you want to get the artist name (same for all the rest , album , title etc..) from a file , and save in into a C string (const char*) , you do it like this :
> TagLib::FileRef f("song.mp3");
TagLib::String artist = f.tag()->artist()

and now that the artist name in saved in a TagLib string type , you convert it to C string by:

> const char* artist = artist.toCString(true);

I dont see a filesize function in FileRef (taglib) but you can do it like this , with the C++ lib :
> #include<iostream>
#include<fstream>
#include<string>
using namespace std;

streamsize file_size(const string& file_name);

int main(int argc , char* argv[]) {
    
    cout<<file_size("Aerosmith - Armaggedon.mp3");
    
    return 0;
}


streamsize file_size(const string& file_name) {
    
    streamsize _size = 0;
    fstream file(file_name.c_str() , ios_base::in | ios_base::binary);
    if (file.is_open()) {
        file.seekg( 0 , ios_base::end);
        _size = file.tellg();
        file.close();
        return _size;
    } else
        return 0;
}

if you have more problem (compiling , linking etc..), i'll be more than happy to help.

---

### Post by Neon612 on 2008-08-11
I tried what you said since it seems to make sense now that I went back and reread the documents from their site. BUt the include statement is the part I'm not sure on, What does it have to be? 

My compile command was:
```
g++ mp3ls.cpp -o mp3
```

And compiling gives me thes errors:
```
mp3ls.cpp: In function &#8216;int main()&#8217;:
mp3ls.cpp:42: error: &#8216;FileRef&#8217; is not a member of &#8216;TagLib&#8217;
mp3ls.cpp:42: error: expected `;' before &#8216;f&#8217;
mp3ls.cpp:43: error: &#8216;f&#8217; was not declared in this scope
mp3ls.cpp:47: error: conflicting declaration &#8216;const char* artist&#8217;
mp3ls.cpp:44: error: &#8216;artist&#8217; has a previous declaration as &#8216;TagLib::String artist&#8217;
mp3ls.cpp:48: error: conflicting declaration &#8216;const char* title&#8217;
mp3ls.cpp:43: error: &#8216;title&#8217; has a previous declaration as &#8216;TagLib::String title&#8217;
mp3ls.cpp:49: error: conflicting declaration &#8216;const char* album&#8217;
mp3ls.cpp:45: error: &#8216;album&#8217; has a previous declaration as &#8216;TagLib::String album&#8217;
```

---

### Post by StOoZ on 2008-08-11
you should Include this :
> -I/usr/local/include/taglib

in the source code its : #include<taglib/tag.h>

and link :
> -L/usr/local/lib -ltag

in case taglib is not installed in the same dirs , just modify the path.

---

### Post by Neon612 on 2008-08-11
My changed compile command:
```
g++ mp3ls.cpp -o mp3 -ltag
```

And I still get the same errors.

---

### Post by kknd on 2008-08-11
g++ file.c -o out `pkg-config --cflags --libs taglib`

---

### Post by StOoZ on 2008-08-11
well I use netbeans so I dont directly type this command , buy try:

> g++ mp3ls.cpp -o mp3 -I/usr/local/include/taglib -L/usr/local/lib -ltag

I have never used that way of compiling , always IDE's for me :(
so I set this things in my IDE.

---

### Post by Neon612 on 2008-08-11
Thanks for your help but so far I still get the same errors. I tried it in Eclpise but I can't figure out how to compile it and my Netbeans copy will not start.

---

### Post by StOoZ on 2008-08-12
ok , how did you install taglib?
in the terminal , please write the following :
> pkg-config --list-all | grep taglib

and write the output.

---

### Post by Neon612 on 2008-08-12
I installed the version in the gutsy repos.

Here's the output:
```
taglib                TagLib - Audio meta-data library
```

---

### Post by Neon612 on 2008-08-14
C'mon people a litle help please!

---

### Post by StOoZ on 2008-08-14
try :
> g++ mp3ls.cpp -o out `pkg-config --cflags --libs taglib`

---

### Post by Neon612 on 2008-08-14
Thank you at least someone is looking around.

Here is the error message I keep getting:
```
mp3ls.cpp: In function ‘int main()’:
mp3ls.cpp:43: error: ‘FileRef’ is not a member of ‘TagLib’
mp3ls.cpp:43: error: expected `;' before ‘f’
mp3ls.cpp:44: error: ‘f’ was not declared in this scope
```

And here is my code (if it will help):
[php]#include <stdio.h>
#include <dirent.h>
#include <string>
#include <iostream>
#include <taglib/tag.h>
//#include <taglib/fileref.h>

using namespace std;

int mp3filter(const struct dirent *dir)     // post: returns 1/true if name of dir ends in .mp3    
{
  	const char *s = dir->d_name;
  	int len = strlen(s) - 4;            // index of start of . in .mp3
  	if(len >= 0)
    	{
      		if (strncmp(s + len, ".mp3", 4) == 0)
    		{
      			return 1;
    		}
    	}
  	return 0;
}

/*static int one (const struct dirent *unused)
{
  	return 1;
}*/

int main ()
{
	string strTemp;
  	struct dirent **eps;
  	int n;

  	n = scandir ("./", &eps, mp3filter, alphasort);
  	if (n >= 0)
    	{
      		int cnt;
      		for (cnt = 0; cnt < n; ++cnt)
      		{
    			strTemp = (eps[cnt]->d_name);
    			
    			TagLib::FileRef f(strTemp);
    			TagLib::String title = f.tag()->title();
    			TagLib::String artist = f.tag()->artist();
    			TagLib::String album = f.tag()->album();
    			
    			/*const char* artist = artist.toCString(true);
    			const char* title = title.toCString(true);
    			const char* album = album.toCString(true);*/
    			
    			//g++ file.c -o out `pkg-config --cflags --libs taglib`
    			
    			cout << title << "-" << artist << " (" << album << ")" << endl;
    			
    			
    			
    			//puts (eps[cnt]->d_name);
    		}
    	}
  	else
  	{
  		perror ("Couldn't open the directory");
  	}

  	return 0;
}  [/php]

---

### Post by StOoZ on 2008-08-15
since FileRef constructor takes a FileName type as an argument...
> FileRef (FileName fileName, bool readAudioProperties=true, AudioProperties::ReadStyle audioPropertiesStyle=AudioProperties::Average)

you cant just give it a string , you need to cast it to C string (const char*) since FileName is this typedef:
> typedef const char* TagLib::FileName

so this call:
>  TagLib::FileRef f(strTemp); 

should be like this:
>  TagLib::FileRef f(strTemp.c_str());

---

### Post by Neon612 on 2008-08-15
Okay htat makes sense.
But I'm still returning the same error. "FileRef is not part of tagLib."

---

### Post by StOoZ on 2008-08-15
btw , what version of taglib are you using?
how did you get it?

---

### Post by Neon612 on 2008-08-15
> **StOoZ said:**
> btw , what version of taglib are you using?
how did you get it?

I think its 1.4 or 1.3. Basically the one from the gutsy repos.

---

### Post by Neon612 on 2008-08-16
bump?

---

### Post by StOoZ on 2008-08-17
I think that , you need to try first to compile a simple  (just load the artist tag for example, and display it) TagLib program , too see that everything works fine.
then move to your program and make the correct fixes.

---

### Post by Neon612 on 2008-08-17
Okay. This is just agravating.

I setup something with just the artist from a particular file and nothing else. Still the same error:
```
mp3.cpp: In function ‘int main()’:
mp3.cpp:12: error: ‘FileRef’ is not a member of ‘TagLib’
mp3.cpp:12: error: expected `;' before ‘f’
mp3.cpp:13: error: ‘f’ was not declared in this scope
mp3.cpp:15: error: conflicting declaration ‘const char* artist’
mp3.cpp:13: error: ‘artist’ has a previous declaration as ‘TagLib::String artist’
```

And I'm using this code:
[php]#include <string>
#include <iostream>
#include <taglib/tag.h>
//#include <taglib/fileref.h>

using namespace std;

int main ()
{
	TagLib::FileRef f("Journey - When The Lights Go Down In The City.mp3");
    	TagLib::String artist = f.tag()->artist();
    	
    	const char* artist = artist.toCString(true);
    	
    	cout << artist << endl;

  	return 0;
}  [/php]

---

### Post by StOoZ on 2008-08-17
weird , I use the latest version from taglib's site , installed it from source, and it works perfect.
try it.. it might solve your problem.
I didnt install it from the repositories, if you need help with that , I can help even in MSN / ICQ

---

### Post by Neon612 on 2008-08-17
From reading their INSTALL documentation I go to the directory where the tarball extracted to, type ./configure, make, and sudo make install. Right?

I looked in the /usr/local/include directory and there is a taglib folder inside. I check the version number, now I have 1.5. But, alas, the same errors keeps on cropping up. Is it a good idea to put the whole directory string in an include statement:

IE: #include </usr/local/include/taglib/taglib.h>

---

### Post by StOoZ on 2008-08-17
try to include the following:
#include<taglib/tag.h>
#include<taglib/fileref.h>
#include<taglib/tstring.h>

and try this :
> g++ mp3ls.cpp -o out `taglib-config --libs --cflags` 

change the filenames (mp3ls.cpp... etc..) if needed.

---

### Post by Neon612 on 2008-08-17
Thank you that part is working but not the const char* declaration is givving me problems. It is saying that artist is already declared:
```
mp3.cpp:16: error: conflicting declaration &#8216;const char* artist&#8217;
mp3.cpp:14: error: &#8216;artist&#8217; has a previous declaration as &#8216;TagLib::String artist&#8217;

```

---

### Post by StOoZ on 2008-08-17
try this :
> 
#include<taglib/tag.h>
#include<taglib/fileref.h>
#include<taglib/tstring.h>
using namespace std;

int main ()
{
    TagLib::FileRef f("Journey - When The Lights Go Down In The City.mp3");
        TagLib::String artist = f.tag()->artist();
        
        const char* artist2 = artist.toCString(true);
        
        cout << artist2 << endl;

      return 0;
}  

btw, im using almost every aspect of taglib in my app that im writing nowadays.
so if you have further questions , feel free , I bet that the code above solved your issue.

---

### Post by Neon612 on 2008-08-17
Thank you that worked perfectly. :)

I had already tried replacing the CString artist with a different variable name before my last post. So I don't exactly know what happened here? I did notice that I included iostream and string. Could the string header file of had anything to do with the problem?

---

### Post by daschmidt on 2008-09-30
Hi! I'm having a similar error with the fallowing code: 

```
#include <taglib/fileref.h>
#include <taglib/tag.h>
#include <taglib/tstring.h>
#include <taglib/taglib.h>

using namespace TagLib;

void method() {

        QString path = "This string came from a songs list";

	String s = String(path.toStdString().c_str());

	FileRef f = FileRef( (FileName) s.toCString(true) );

	QString artist(TStringToQString(f.tag()->artist()));

	QString album(TStringToQString(f.tag()->album()));

}
```

```
error: ‘FileName’ was not declared in this scope.
```

and also:

```
/usr/include/taglib/fileref.h:107: error: ‘File’ declared as a ‘virtual’ field
/usr/include/taglib/fileref.h:107: error: expected ‘;’ before ‘*’ token
/usr/include/taglib/fileref.h:127: error: expected `)' before ‘fileName’
/usr/include/taglib/fileref.h:136: error: expected `)' before ‘*’ token
/usr/include/taglib/fileref.h:179: error: expected ‘;’ before ‘*’ token
/usr/include/taglib/fileref.h:216: error: ‘StringList’ does not name a type
/usr/include/taglib/fileref.h:250: error: expected ‘;’ before ‘*’ token
```

If I try to instantiate the FileRef without that FileName cast the following error emerges:

```
error: no matching function for call to ‘TagLib::FileRef::FileRef(const char*)
```

Thanks for any help in advance.

---

