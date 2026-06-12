---
title: "Detect UTF-16, UTF-8 chars in Java"
date: 2009-11-14
forum: Programming Talk
---

### Post by andrew222 on 2009-11-14
Hello,

I wanted to ask if anyone knows if in the Java 1.4 API there is a mechanism to find out if a character is UTF-16 or UTF-8?

I am reading about checking a character's bytes, but i can't seem to find something about how to check this in the API yet.

---

### Post by Reiger on 2009-11-14
At least you can do something like this:

```

public static boolean isCharset(String encName, byte[] expected, String sample) {
  try {
    byte[] bs = sample.getBytes(encName);
    for(int i=0; bs[i] == expected[i] && i<bs.length; ++i) {
      // nothing to see here, everything is done in the condition above
    }
    return i==bs.length && bs.length == expected.length;
  }
  catch(Exception e) {
    return false;
  }
}
```

---

### Post by The Cog on 2009-11-15
A character is neither utf8 or utf16. A character is a character - a 16-bit unsigned value. And a String contains a sequence of characters, so Strings aren't utf8 or utf16 either. 

utf8 and utf16 are ways of encoding character values into byte sequences. I'm not aware of any reliable way to tell if a byte array is utf8 or utf16 except that utf16 will often contain lots of 00 bytes in alternate locations (odd or even depending on whether it's big-ended or little-ended). You could try decoding into a string and see if you get an exception thrown, which would indicate that you just guessed wrong.

---

