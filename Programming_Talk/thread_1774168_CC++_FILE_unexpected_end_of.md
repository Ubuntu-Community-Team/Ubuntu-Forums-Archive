---
title: "C/C++ FILE* unexpected end of"
date: 2011-06-03
forum: Programming Talk
---

### Post by josh. on 2011-06-03
Hi guys,
Im trying to create a program to read in a .wav file. So far i have it processing the header and starting the data and all is good. However, for some reason my file pointer reaches the end of the file earlier than expected. in fact the file has ~13mil samples and it only gets through ~1100 of the samples.
I initialise my FILE as:

FILE* AudioFile;
AudioFile = fopen(filepath,"r");

where filepath is a string to the directory.
I then read in the file in a loop as such:

unsigned char buffer;
while(has more bytes)
{
fread(&buffer,1,1,AudioFile);
}

and then use the char stored in buffer as required. My problem is as i said above that after about 1000 samples, AudioFile thinks it has reached the end of the file even though there are clearly millions more samples to process. Does anyone know why this might be? Any help is greatly appreciated

EDIT:
I also tried the following code:
AudioFile = fopen(filepath,"r");
fseek( AudioFile, 0L, SEEK_END );
cout << ftell( AudioFile ) << endl;
rewind(AudioFile);
And got a value of around 26 mil, which would be expected as each sample is 2 bytes. This however has further confused me, as the file obviously knows its got that many bytes, so i don't know why it seems to think it reaches the end of the file at about 100 samples.

---

### Post by ve4cib on 2011-06-03
What's your condition in the loop?  CONDITION isn't terribly helpful from a debugging perspective...

---

### Post by josh. on 2011-06-03
yea i didn't bother putting it in cos i know my loop isnt restricting the file reading, but the actual loop i have is:
```

	unsigned char buffer;
	unsigned int tmp;

	for (unsigned int i=0; i < SampleCount; ++i)
	{
		tmp = 0;

		for (unsigned int j=0; j != BitsPerSample; j+=8 )
		{
			if(feof(AudioFile))
			{
				//cout << "*********" << endl;
			}
			fread(&buffer,1,1,AudioFile);
			tmp += buffer << j;
		}

		data[i] = ConvertBitSize(tmp, BitsPerSample);
	}

```
where ConvertBitSize is just a function to account for 2's compliment conversion. 
Sample count = 13408128
BitsPerSample = 16
which are obtained from the header

As you can see i have a if(feof(AudioFile)) statement there for the purposes of debugging. The fact that after the ~1000 samples i was getting all ******* outputs tells me it thinks its at the end of the file

---

### Post by ve4cib on 2011-06-03
Small request, but next time you post code could you put it in [ code ]...[/ code ] tags?  It makes it way easier to read.

Anyway, as for your problem, I am a little bit stumped.  I've never used feof before, so I'm not entirely sure what it looks for when determining if it should return TRUE or FALSE.

My first guess is that you may be running into a problem of the function looking for an EOF character.  That works fine when opening a text file, but breaks when opening binary data (since the EOF byte could very well be "real" data in a binary format).

What happens if you try opening a text file and loop through it with your code?  Even something as stupid as creating a base-64 copy of the audio file you're trying to read?

Just to reiterate, this is a largely uneducated guess as to what the problem *could* be.  I could very easily be completely wrong.

---

### Post by josh. on 2011-06-03
Sorry, I'm a forum noob, this is the first post i have made, but i appreciate the advise and have edited my previous post to make it more readable.

As for feof, my understanding is that it checks a flag within the FILE object to see if it has been set to true, signifying the end of file. I have been struggling very very much to find good documentation on how this basic c I/O works! It appears that several functions of the 'cstdio' library such as 'fread' that i am using, have power to set the eof flag to true however im unsure, as you said you too are, of how this decision is made. You may have seen i added to my first post an edit where i computed the length of the file, which came up with the expected number of bytes, so it seems contradictory that the eof flag is being set prematurely.

I tried also using fstream and other functions from the IOstream library, however i ran into similar problems, with the added difficulty of having to read my bytes in as 'chars' and not 'unsigned chars'.

I shall try testing my IO on a text file rather than a wav and see if i run into similar difficulties!

---

### Post by josh. on 2011-06-04
I opened the wav file in hex editor neo and saved it as a txt file. I tried running it throught my prgram but came to the same problem :S this has really got me stumped!!

---

### Post by josh. on 2011-06-04
I think i have figured out my problem!!!! I told the file to open in binary mode
```
AudioFile = fopen(filepath,"rb");
```
not
```
AudioFile = fopen(filepath,"r");
```
And it appears to be much happier now! Thanks for your help :)

---

### Post by dwhitney67 on 2011-06-04
> **josh. said:**
> I think i have figured out my problem!!!! I told the file to open in binary mode
```
AudioFile = fopen(filepath,"rb");
```
not
```
AudioFile = fopen(filepath,"r");
```
And it appears to be much happier now! Thanks for your help :)

There's more to the problem, at least what I can observe from the code you posted.

Rather than relying on feof(), leverage the use of the return value from fread().  If you reach the end of the file, fread() will return a value of zero (0).

As for the EOF flag that is reported by feof(), it does not get set to "true" until your program performs a read operation that actually reaches the end of the file.

Here's a sample program that tests this fact:
```

#include <stdio.h>

int main()
{
   FILE* fp = fopen("/etc/hosts", "r");
   char  ch;

   while (!feof(fp))
   {
      size_t rtn = fread(&ch, 1, sizeof(ch), fp);

      if (rtn > 0)
      {
         printf("%c", ch);
      }
      else
      {
         /* If feof() had done it's job, we would not be here! */
         printf("Oops; reach the end of the file.\n");
      }
   }
   printf("\n");
   return 0;
}

```


Lastly, you should refrain from mixing C and C++ programming together.  Everything you coded could have been done in pure C++ without the feof(), fopen(), fread(), etc.  The istream class, from which ifstream is derived, supports all of these capabilities.


P.S.  I should have stated earlier that the way to avoid feof() is to do something like:
```

   ...

   size_t rtn = 0;
   char   ch;

   while ((rtn = fread(&ch, 1, sizeof(ch), fp)) > 0)
   {
      /* do something with ch */
   }

```

---

### Post by josh. on 2011-06-04
I wasn't really relying on the feof() for anything functional in my code but rather to debug and see what might have been causing the odd behaviour, but if i had been that would be a valid point! I think by not reading the file in binary, the fread() was returning 0 before it reached the true end of the file, which i have no explanation for! :S

And i am indeed relatively new to c and c++ and don't know much about the conventions of the language and that sorta thing so i appreciate the point you made about using the istream class. However as you may have seen in a previous post i did in fact try using the ifstream, however i was needing to do alot of casting from char to unsigned char as read() can only take in a char* unlike the fread() which can take in an unsigned char*. Would you recommended that it would be better to us the ifstream and just do the casts where required to avoid the mixing up of c and c++??

---

### Post by dwhitney67 on 2011-06-04
> **josh. said:**
> Would you recommended that it would be better to us the ifstream and just do the casts where required to avoid the mixing up of c and c++??

I was merely recommending that you stick with one language, and not mix the two.

If a binary file needs to be read in C++, then for obvious reasons the storage buffer would be declared as an unsigned char.  As for casting, yes you are correct; it would need to be done.

Here's a simple example:
```

#include <fstream>
#include <cassert>

int main()
{
   std::fstream  iFile("/vmlinuz.old", std::ios::in | std::ios::binary);
   std::fstream  oFile("copy-vmlinuz.old", std::ios::out | std::ios::binary);
   unsigned char buffer[1024];

   // lame error checking
   assert(iFile.good() == true);
   assert(oFile.good() == true);

   while (iFile.good())
   {
      iFile.read(reinterpret_cast<char*>(buffer), sizeof(buffer));

      if (iFile.gcount() > 0)
      {
         oFile.write(reinterpret_cast<const char*>(buffer), iFile.gcount());
      }
   }
}

```
Note, that due to my personal preference, I use std::fstream in lieu of the more formal std::ifstream and std::ofstream.

---

