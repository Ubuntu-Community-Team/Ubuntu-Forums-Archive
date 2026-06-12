---
title: "How to scan [ and ] with fscanf?"
date: 2010-06-14
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2010-06-14
I wrote some C code:
[php]
if ( fscanf( fp, "[%s]", buf ) != 1 )
{
	snprintf( error_msg, sizeof(error_msg), "%s", strerror(errno) );
	return 0;
}
[/php]
It always fails, with error message "Success", because [ and ] have special meaning. It should parse text like this:
> 
[globals]

How to make fscanf read [ and ] just like any normal character?

---

### Post by gmargo on 2010-06-14
There's nothing special about brackets in a scanf string, unless the opening bracket is preceded by a percent sign(%).  You have some other problem with your input stream.  You can prove this to yourself by changing the bracket to some other character, like 'A'.

BTW, your scanf won't work right anyway since the %s matches up to the next whitespace; it will not stop at the closing bracket.

---

### Post by dwhitney67 on 2010-06-14
> **crazyfuturamanoob said:**
> 
How to make fscanf read [ and ] just like any normal character?
As indicated already, the [] brackets are normal characters.

I would suggest you read in the entire line, including the brackets, into a temporary buffer.  Then parse the buffer using strtok().

For example:
```

char  buf[80] = {0};
char* tag = 0;

if (fscanf(fp, "%s", buf) == 1)
{
   tag = strtok(buf, "[]");

   if (!tag)
   {
      /* error; no tag found */
   }
}
else
{
   /* error w/ fscanf() */
}

...

```

P.S.  If you know the length of the string within the [] ahead of time, then you can specify how many characters within the fscanf() format statement, but IMO, this is crude.
```

fscanf(fp, "[%6s]", buf);

```

---

### Post by crazyfuturamanoob on 2010-06-14
Before I read dwhitney's post I wrote this:
```

void read_until( FILE *fp, int x )
{
	int ch;
	while( (ch=fgetc(fp)) != EOF && ch != x );
}


static int read_section_name( FILE *fp, iniSection *section, char *filename )
{
	char buf[128];
	long start, end, length;
	char too_long = 0;
	
	read_until( fp, '[' );
	start = ftell( fp );
	read_until( fp, ']' );
	end = ftell( fp ) - 1;
	
	length = end - start;
	
	if ( length >= sizeof(buf) )
	{
		length = sizeof( buf );
		too_long = 1;
	}
	
	fseek( fp, start, SEEK_SET );
	fread( buf, length, 1, fp );
	buf[length] = '\0';
	
	section->name = strdup( buf );
	
	if ( section->name == NULL )
	{
		snprintf( error_msg, sizeof(error_msg), "%s", strerror(errno) );
		return 0;
	}
	
	if ( too_long )
	{
		fprintf( stderr, "Warning: too long section name in %s: \"%s\"...\n", filename, section->name );
		fprintf( stderr, "Maximum section name length: %lu\n", sizeof(buf) - 1 );
	}

	read_until( fp, '\n' );
	
	return 1;
}

```

Edit: Sometimes that function doesn't work. It thinks the string length is >127 when it isn't and prints the warning messages? I will try a mix of above and scanf.

---

### Post by soltanis on 2010-06-14
```

// scanf("%[^[][%[^]]]%s", before, inside, after); NO
ret = scanf("[%[^]]]", inside); // YES

```

From man 3 scanf:

```


       %[     Matches a non-empty sequence of characters  from  the  specified
              set  of  accepted characters; the next pointer must be a pointer
              to char, and there must be enough room for all the characters in
              the  string,  plus  a  terminating null byte.  The usual skip of
              leading white space is suppressed.  The string is to be made  up
              of  characters  in  (or  not  in)  a  particular set; the set is
              defined by the characters between the open bracket  [  character
              and a close bracket ] character.  The set excludes those charac&#8208;
              ters if the first character after the open bracket is a  circum&#8208;
              flex  (^).   To  include a close bracket in the set, make it the
              first character after the open bracket or  the  circumflex;  any
              other position will end the set.  The hyphen character - is also
              special; when placed between two other characters, it  adds  all
              intervening characters to the set.  To include a hyphen, make it
              the  last  character  before  the  final  close  bracket.    For
              instance,  [^]0-9-]  means  the  set  "everything  except  close
              bracket, zero through nine, and hyphen".  The string  ends  with
              the appearance of a character not in the (or, with a circumflex,
              in) set or when the field width runs out.

```

No need to use strtok or any ugliness like that.

---

### Post by dwhitney67 on 2010-06-14
> **soltanis said:**
> ```

scanf("%[^[][%[^]]]%s", before, inside, after);

```

From what I understand from the man-pages and other sources, you are correct about being able to have scanf (or fscanf) disregard certain chosen character(s), and yet accept others.  So yes, this would be better than doing the strtok() approach.

Now, if we could only get the code you have presented above to actually work, then the OP would be in business.  Is there perhaps a typo in the format statement?

---

### Post by dwhitney67 on 2010-06-14
> **dwhitney67 said:**
> 
Now, if we could only get the code you have presented above to actually work, then the OP would be in business.  Is there perhaps a typo in the format statement?

Got it...
```

char dontCare[2] = {0};
char tag[80] = {0};

int ret = fscanf(fp, "%[[]%[^]]", dontCare, tag);

assert(ret == 2);

```

P.S.  The code above assumes the string "[globals]" is read from the file.

---

### Post by soltanis on 2010-06-15
Actually, you're right, but you need not use a dummy variable or a format conversion at all. Use the format string, Luke:

```

ret == fscanf(fp, "[%[^]]", tag);
assert(ret == 1);

```

I've tested that and it does work on extracting any string from inside some []'s. Of course, it assumes that the next string is enclosed in brackets and will abort if it isn't (but that's a good reason to test the return value of the function).

---

### Post by crazyfuturamanoob on 2010-06-15
I solved it in a different way:
```

static int read_section_name( FILE *fp, iniSection *section, char *filename )
{
	char buf[128];
	
	fgetc( fp ); // [
	fgets( buf, sizeof(buf), fp );
	strchr( buf, ']' )[0] = '\0';

	section->name = strdup( buf );
	if ( section->name == NULL )
	{
		SET_ERROR_FROM_ERRNO( errno );
		return 0;
	}
	
	return 1;
}

```

I tested it and it works. PS. The next string is not enclosed in brackets so the above solution does not work.

Thanks for the replies. :)

---

