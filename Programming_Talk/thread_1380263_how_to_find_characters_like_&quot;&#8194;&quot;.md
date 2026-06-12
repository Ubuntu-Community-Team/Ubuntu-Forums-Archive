---
title: "how to find characters like: &quot;&#8194;&quot;?"
date: 2010-01-13
forum: Programming Talk
---

### Post by giuspen on 2010-01-13
Hi,
I'm working on a rich text editor based on xml that in case I paste characters like the following: "&#8194;" crashes.
Is there a way I can recognize those characters?
I have not idea what they are and how to search them in the text.
Thanks in advance.

---

### Post by Habbit on 2010-01-13
Those (0x04 and 0x05) are control characters, which do not have a printable representation. Most are a relic from the teletype age, currently unused, and so you can see them sometimes doubling as record markers or separators. Others, like NUL (0x00), CR (0x10) or LF (0x13) are still in wide use. On the other hand, you might also see "squares" representing a character for which the font you are using has no glyph to display (maybe some in "&#1240;&#33603;&#12366;&#42119;").

About your question, the XML editor should not _crash_ on them, but using those characters (other than CR LF) directly in an XML document is not the best practice, precisely because they might be mistaken for others, not be displayable in all fonts, etc. You can use references like &#x1f60; for "&#8032;".

---

### Post by giuspen on 2010-01-13
> **Habbit said:**
> Those (0x04 and 0x05) are control characters, which do not have a printable representation. Most are a relic from the teletype age, currently unused, and so you can see them sometimes doubling as record markers or separators. Others, like NUL (0x00), CR (0x10) or LF (0x13) are still in wide use. On the other hand, you might also see "squares" representing a character for which the font you are using has no glyph to display (maybe some in "&#1240;&#33603;&#12366;&#42119;").

About your question, the XML editor should not _crash_ on them, but using those characters (other than CR LF) directly in an XML document is not the best practice, precisely because they might be mistaken for others, not be displayable in all fonts, etc. You can use references like &#x1f60; for "&#8032;".

Hi and thanks for explanation.
I was wandering if there is a way to recognize a character as "without printable representation" by code, maybe in python, as once found the guilty characters it would be easy for me to get rid of it.

---

### Post by giuspen on 2010-01-13
if anybody interested, seems I found a solution of the removal of those characters with the following python line of code:
[PHP]cherrytree_string = re.sub("[\x00-\x08\x0b-\x1f]", "", cherrytree_string)[/PHP]

---

