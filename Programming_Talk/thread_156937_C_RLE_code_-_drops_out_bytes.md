---
title: "C RLE code - drops out bytes"
date: 2006-04-08
forum: Programming Talk
---

### Post by Landser on 2006-04-08
Hello, 

I'm currently working on a portable RLE algorithm in C ..
I already have some working code but the problem is that it just drops one
byte after 2 matching bytes ... For example "Hello" becomes "Hell" ](*,)  

```
int RLE_CompressFile(char* in, char* out)
{
	FILE* fin;
	FILE* fout;

	char LastChar, ThisChar;
	int repeats = 0;

	if ( (fin = fopen(in, "rb")) == NULL ) {
		printf("Error opening file %s\n", in);
		return 0;
	}
	if ( (fout = fopen(out, "wb")) == NULL ) {
		printf("Error opening file %s\n", out);
		fclose(fin);
		return 0;
	}
	
	LastChar = fgetc(fin);		/** Get 2 bytes **/
	ThisChar = fgetc(fin);

	for (;;) {
		repeats = 0;
		printf("pos: %d\n", ftell(fin));
		printf("%c", LastChar);
		printf("%c\n", ThisChar);

		if (LastChar == ThisChar) {
			fputc(LastChar, fout);
			fputc(ThisChar, fout);

			while (ThisChar == fgetc(fin) ) {
				repeats++;
			}


			fputc(repeats, fout);
			LastChar = fgetc(fin);		/** Get 2 bytes **/
			ThisChar = fgetc(fin);

			
		}
		else {
			fputc(LastChar, fout);
			LastChar = ThisChar;
			ThisChar = fgetc(fin);
			
		}

		if (ThisChar == EOF) break;

	}



	fclose(fin);
	fclose(fout);
}
```

I'm a bit advanced in C.. But I still don't understand why
something like this happens.. Can someone explain this to me?

---

### Post by xenmax on 2006-04-08
I am no expert in C, but[FONT=monospace]
[/FONT]```
fputc(repeats, fout);
```
this tries to write a char to your o/p file which will be a ASCII char corresponding to integer value.
Example: If your input file has a char repeating say 65 times, your output file will probably contain ASCII equivalent of decimal 65 which is 'A'.

---

### Post by Landser on 2006-04-08
Well, I already got it fixed... I just added fseek(fin, ftell(fin)-1, SEEK_SET); before
fputc(repeats, fout); .. The byte-repeat loop before it reads 1 byte more
than expected which causes such things to happen...

Hmm.. I thought I would get a lot of replys to my C question, aren't most advanced linux users C geeks?.. Or gurus?

Thanks for the reply anyway :rolleyes:

---

