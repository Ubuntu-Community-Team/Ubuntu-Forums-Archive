---
title: "[C] Infinite Loop... but why?"
date: 2008-04-23
forum: Programming Talk
---

### Post by nvteighen on 2008-04-23
Hi there!

I'm writting a little Vigenère cipher encoder and it **primarily** works, if the input file only includes letters. I want it to just skip and ignore any non-alphabetic data, not even saving them into the buffer array. But for some reason I don't know the loop I'm using to read & filter out is getting me into an infinite loop and don't know why... I just could (fortunately) isolate the error and discover where it is.

Here's the function. The loop is the last part of it:
[PHP]
int ReadFile(FILE **SourceFile, char **OutputStream, char *path)
{
	*SourceFile = fopen(path, "r+");
	/*I need to write then later, so "r+"*/
	if(*SourceFile == NULL)
	{
		puts("BBB"); /*Going to change this...!*/
		exit(2);
	}

	int length = 0;
	char c = 0;
	while(fscanf(*SourceFile, "%c", &c) != EOF)
		length++;
	/*Yes, primitive way to determine data length, but don't know
	 *any better! It's not the smartest, I recognize it.
	 */
	rewind(*SourceFile); /*Rewinding*/
	*OutputStream = malloc(length * sizeof(*OutputStream));
	if(*OutputStream == NULL)
		exit(2); /*Yes, this should also be changed to include
			  *error output, but I leave that to the last
			  */

	/*BUGGY LOOP! Here we are*/
	c = 0; /*Reusing the same variable as before*/
	int i = 0;
	while(i < length)
	{
		fscanf(*SourceFile, "%c", &c);
		if(isalpha(c))
		{
			/*Only pass the read char if it's a letter.
			 *If not, index should be kept intact and the 
			 *character read.
			 */
			(*OutputStream)[i] = tolower(c) - 'a';
			i++;
		}
	}

	return length; /*Yes: this is in purpose! I want to avoid globals*/
}
[/PHP]

Thanks in advance! Happily the rest works flawlessly; it's just this detail which is blocking the last step.

---

### Post by Can+~ on 2008-04-23
if "c" is not alphanumeric, the i doesn't increase, the while gets stuck at that position, fscanf advances again to read the next one. So eventually, even if you end the length of the file, the "i" will be lower than the length.

Solution: Move the "i++" outside of the if (isalpha()) { }

Alternate: Or read the file until EOF. (!feof(*FILE stream))

---

### Post by johnl on 2008-04-23
Just a side note:  you can do the following to determine the length of the file without reading through it character by character (see 'man fseek')

```

// seek to end of file
fseek(*SourceFile, 0, SEEK_END);
// get the current position in the file, which will be
// equivalent to the file length since we're at the end.
long fileLen = ftell(*SourceFile);
// go back to the beginning of the file.
rewind(*SourceFile);

```

---

### Post by bite on 2008-04-23
You are not increasing your loop variable 'i' when !isalpha(c). So no surprise that the loop never reaches its end when reading non alphabetic characters.

---

### Post by Lux Perpetua on 2008-04-23
You only increment **i** for each alphabetic character, of which there are actually fewer than **length** if there are any non-alphabetic characters in the file. Thus, **i** can never attain the value **length** in that case.

---

### Post by nvteighen on 2008-04-23
> **Can+~ said:**
> if "c" is not alphanumeric, the i doesn't increase, the while gets stuck at that position, fscanf advances again to read the next one. So eventually, even if you end the length of the file, the "i" will be lower than the length.

Solution: Move the "i++" outside of the if (isalpha()) { }

Alternate: Or read the file until EOF. (!feof(*FILE stream))

Thanks! The second one works as I needed. The first one leaves zeros inside the array that corrupt the plaintext (I already had tried that).

> **johnl said:**
> Just a side note:  you can do the following to determine the length of the file without reading through it character by character (see 'man fseek')
(...)

Thanks too! I'm going to look up this and use it; seems much more reasonable than the char-by-char.

EDIT: How am I supposed to mark this as [SOLVED] in the new forums interface??

---

### Post by Can+~ on 2008-04-23
You can't mark as solved yet, but it will be fixed.

---

