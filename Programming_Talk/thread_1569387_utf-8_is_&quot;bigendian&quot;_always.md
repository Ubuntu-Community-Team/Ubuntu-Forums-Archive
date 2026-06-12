---
title: "utf-8 is &quot;bigendian&quot; always"
date: 2010-09-06
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-06
I just been coding utf-8 coding/decoding...

It seems that this is always serialized with most significant byte first... or is it platform dependent?

I wonder what happens when we get Right to Left languages? Do we store all the lines back to front or is it the display that reverses cursor direction and does carriage returns to the right margin :confused:

---

### Post by NovaAesa on 2010-09-06
utf-8 doesn't need to know anything about endianness because each unit is a single octet.

---

### Post by worksofcraft on 2010-09-06
> **NovaAesa said:**
> utf-8 doesn't need to know anything about endianness because each unit is a single octet.

Lol - OK... what I meant is does utf-8 always serialize the unicode values by putting the most significant byte of the unicode value in the first octet of it's output and then the lower bits in subsequent follow up bytes?

---

### Post by NovaAesa on 2010-09-06
Yes, the most significant bits of the code point always go into the bytes near the start of the sequence (for code points that must be encoded in more than one octet).

If you have a code point, you can't just break it into bytes and put them in though, you have to worry about controls bits and such that go at the start of each octet. It's not a direct copy-and-paste mapping between code point and encoded unicode value.

---

### Post by worksofcraft on 2010-09-06
> **NovaAesa said:**
> ...you have to worry about controls bits and such that go at the start of each octet.

thanks :)
You see I want to work with strings of char that contain utf-8 but handle "wide characters" in my code. So I'm encoding and decoding as I process like follows. Just wasn't sure if the order of octets is guaranteed.

```

#include <wctype.h>
#include <stdio.h>

// 0xxxx - ascii compatible byte
// 10xxx - continuation byte, cannot be first
// 110xx - 2 byte sequence 9 bits must be > 0x7F: 0xC0
// 1110x - 3 byte sequence 0xE0
// 11110 - 4 byte sequence 0xF0

const unsigned REPLACEMENT = 0xFFFD;
const unsigned long MAX1UTF8 = 0x80L;
const unsigned long MAX2UTF8 = 0x800L;
const unsigned long MAX3UTF8 = 0x10000L;
const unsigned long MAXUTF8 = 0x110000L;
const unsigned long MAX4UTF8 = 0x200000L;

// count number of unicode characters (i.e after decoding utf8 sequences)
// does not advance the pointer.
unsigned utf8len(const char *S) {
	unsigned That = 0;
	while (get_utf8(S)) ++That;
	return That;
}

static bool receive(wchar_t &Val, const char * &Src) {
	unsigned char C = (unsigned char) *Src++; // avoid sign extend
	// premature terminator or not a continuation byte
	if (!C || (C & 0xC0) != 0x80) {
		fprintf(stderr, "unexpected continuation byte %X\n", (unsigned) C);
		--Src; // stick on error, aborts sequence to try again
		Val = REPLACEMENT;
		return false;
	}
	Val = (Val << 6) + (C & 0x3F); // 6 new bits
	return true;
}

wchar_t get_utf8(const char * &Src) {
	wchar_t That = (unsigned char) *Src++; // avoid sign extend
	if (That == '\0') {
		--Src;
		return That; // stick on valid terminator
	}
	if (That < MAX1UTF8) return That; // valid 7 bit ASCII

	if (!(receive(That, Src))) return That; // incorrect continuation
	if (!(That & MAX2UTF8)) { // 2 byte?
		That &= (MAX2UTF8 - 1);
		if (That >= MAX1UTF8) return That;
		else return REPLACEMENT; // illegal long sequence
		// Note: coding values longer than necessary may be an attempt
		// to bypass securirity e.g. forcing a null terminator mid string
	}
	if (!(receive(That, Src))) return That;
	if (!(That & MAX3UTF8)) { // 3 byte?
		That &= (MAX3UTF8 - 1);
		if (That >= MAX2UTF8) return That;
		else return REPLACEMENT;
	}
	if (!(receive(That, Src))) return That; // incorrect continuation
	if (!(That & MAX4UTF8)) { // 2 byte?
		That &= (MAX4UTF8 - 1);
		if (That >= MAX3UTF8 && That < MAXUTF8) return That;
		else return REPLACEMENT;
	}
	fprintf(stderr, "UTF8 Sequence too long %X\n", That);
	return REPLACEMENT;
}

static bool send(wchar_t C, char * &Dst) {
	if (C > 0x3F) send(C >> 6, Dst);
	*Dst++ = (C & 0x3F) + 0x80; // lsb is last in UTF-8 serialization
	return true;
}

// http://en.wikipedia.org/wiki/UTF-8
bool put_utf8(wchar_t C, char * &Dst, char *End) {
//printf("put_utf8(%lu=%c)\n", C, (char) C);
	if (--End <= Dst) return false;
	if (C < MAX1UTF8) {
		*Dst++ = C;
		return true;
	}
	if (C >= MAXUTF8) C = REPLACEMENT;

	if (--End <= Dst) return false;
	if (C < MAX2UTF8) {
		*Dst++ = (C >> 6) + 0xC0;
		return send(C & 0x3F, Dst);
	}

	if (--End <= Dst) return false;
	if (C < MAX3UTF8) {
		*Dst++ = (C >> 12) + 0xE0;
		return send(C & 0xFFF, Dst);
	}

	if (--End <= Dst) return false;
	*Dst++ = (C >> 18) + 0xF0;
	return send(C & 0x3FFFF, Dst);
}

```

---

### Post by NovaAesa on 2010-09-06
> **worksofcraft said:**
> Just wasn't sure if the order of octets is guaranteed.As I understand it, the order of octets is guaranteed.

---

### Post by Reiger on 2010-09-06
> 
Q: Is the UTF-8 encoding scheme the same irrespective of whether the underlying processor is little endian or big endian?

A: Yes. Since UTF-8 is interpreted as a sequence of bytes, there is no endian problem as there is for encoding forms that use 16-bit or 32-bit code units. Where a BOM is used with UTF-8, it is only used as an ecoding signature to distinguish UTF-8 from other encodings — it has nothing to do with byte order. 
From the official Unicode FAQ: [http://unicode.org/faq/utf_bom.html](http://unicode.org/faq/utf_bom.html)

---

### Post by worksofcraft on 2010-09-07
> **Reiger said:**
> From the official Unicode FAQ: [http://unicode.org/faq/utf_bom.html](http://unicode.org/faq/utf_bom.html)

Tyvm, that is indeed a very useful link :)

---

