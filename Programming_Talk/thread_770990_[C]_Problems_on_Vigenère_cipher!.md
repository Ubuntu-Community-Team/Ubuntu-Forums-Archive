---
title: "[C] Problems on Vigenère cipher!"
date: 2008-04-27
forum: Programming Talk
---

### Post by nvteighen on 2008-04-27
Hi there again!
I'm still working on the same as in [http://ubuntuforums.org/showthread.php?t=764079]("http://ubuntuforums.org/showthread.php?t=764079").

For some reason I don't get, I'm corrupting the encrypted file in an unrecoverable way. <edit>If you don't know about Vigenère: look its [Wikipedia article]("http://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher")</edit>

Can someone point me what am I not doing right?

Yes, in the other thread I said it "primarly worked"; well, now it stopped working. Quite frustrating, but I just don't want to give up.

Here's the Encryption/Decryption function, which is I think where the issue is. If necessary, I can post the whole code.

[PHP]
void EnDecrypt(FILE **SourceFile, char *PlainText,
				int PlainTextLength, char *Key,
				int KeyLength, char option)
{
	rewind(*SourceFile); /*Rewinding file*/
	int i, a = 0;
	char buf = 0;
	for(i = 0; i < PlainTextLength; i++)
	{
		if(option == 'e') /*if users wants to encrypt*/
			buf = PlainText[i] + Key[a];
		else if(option == 'd') /*if user wants to decrypt*/
			buf = PlainText[i] - Key[a];

		fprintf(*SourceFile, "%c", buf);

		a++;
		if(a > KeyLength)
			a = 0;
	}
}
[/PHP]

Thanks!

---

### Post by jpages on 2008-04-27
Hi,

I think that there is a problem in the two following lines :

```
 buf = PlainText[i] + Key[a]; 
```
and
```
 buf = PlainText[i] - Key[a]; 
```

For example, with the second line, the result of PlainText[i] - Key[a] could be negative.

The right lines should be (if we assume that the text is composed of lower case letters):

```
 buf = ((PlainText[i] - 97) + (Key[a] - 97)) % 26; 
```
and
```
 buf = ((PlainText[i] - 97) - (Key[a] - 97)) % 26; 
```

---

### Post by scourge on 2008-04-27
In addition to what jpages suggested, it seems that you should change this:
```

if(a > KeyLength)
    a = 0;

```
To this:
```

if (a >= KeyLength)
    a = 0;

```

That's because 'a' is a zero-based index and KeyLength, I assume, is the number of characters in the key.

It also seems that you don't need a pointer to the FILE pointer ('SourceFile').

And as a matter of style most people would discourage you from writing comments like /*Rewinding file*/ when it's already obvious.

---

### Post by nvteighen on 2008-04-28
> **jpages said:**
> 
(...)
```
 buf = ((PlainText[i] - 97) + (Key[a] - 97)) % 26; 
```
and
```
 buf = ((PlainText[i] - 97) - (Key[a] - 97)) % 26; 
```

(Yes I pass everything through tolower() before en/decrypting) I tried this before and it's still corrupting data... I've found out that it gets out of UTF-8 and is only readable by ISO- I'm suspecting maybe fprintf(..., "%c",...) could have some fault on this. I know it would be much easier to use numbers, but then it wouldn't be Vigenère!

> **scourge said:**
> In addition to what jpages suggested, it seems that you should change this:
```

if(a > KeyLength)
    a = 0;

```
To this:
```

if (a >= KeyLength)
    a = 0;

```

That's because 'a' is a zero-based index and KeyLength, I assume, is the number of characters in the key.

It also seems that you don't need a pointer to the FILE pointer ('SourceFile').

And as a matter of style most people would discourage you from writing comments like /*Rewinding file*/ when it's already obvious.

Well, doing that change it makes the file unreadable only after decrypting.

The pointer-to-pointer wasn't needed too. Thanks for that, it simplifies like a lot.

And I'll take note on your style note! :)

---

### Post by dwhitney67 on 2008-04-28
For fun I decided to implement a version of the Vigenere algorithm.  Initially I also had trouble getting the decryption algorithm to work, but finally sorted it out.  Here's a snip of the code (in C++) I implemented to get it to work:
[PHP]
std::string ResizeKey( const std::string &key, const size_t desiredLength )
{
  std::string resizedKey = key;

  while ( resizedKey.length() < desiredLength )
  {
    resizedKey += resizedKey;
  }
  resizedKey.resize( desiredLength );

  return resizedKey;
}


std::string EncryptDecrypt( enum Action action, const std::string &text, const std::string &key )
{
  std::string resizedKey = ResizeKey( key, text.length() );
  std::string returnText;
  returnText.resize( text.length() );

  for ( unsigned int i = 0; i < text.length(); ++i )
  {
    if ( action == ENCRYPT )
    {
      returnText[i] = (((text[i] - 65) + (resizedKey[i] - 65)) % 26) + 65;
    }
    else  // action == DECRYPT
    {
      int diff = (text[i] - 65) - (resizedKey[i] - 65);

      if ( diff < 0 )
        diff += 26;

      returnText[i] = (diff % 26) + 65;
    }
  }

  return returnText;
}[/PHP]

Hopefully this helps.

P.S.  It might be prudent to surround access to each character with a toupper() call since it appears that Vigenere was/is designed to work with only capital letters.

---

