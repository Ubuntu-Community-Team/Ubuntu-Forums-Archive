---
title: "Parser error"
date: 2015-06-07
forum: Packaging and Compiling Programs
---

### Post by satimis on 2015-06-07
Hi all,

Parser error

On browsing following page'
[http://piano3.satimis.com/a-passion-for-three/](http://piano3.satimis.com/a-passion-for-three/)
```

Warning: SimpleXMLElement::__construct(): Entity: line 1: parser error : Start tag expected, '<' not found in /home/gopublic2014/public_html/piano3/wp-content/plugins/youtube-simplegallery/youtube_simplegallery.php on line 64

Warning: SimpleXMLElement::__construct(): No longer available in /home/gopublic2014/public_html/piano3/wp-content/plugins/youtube-simplegallery/youtube_simplegallery.php on line 64

Warning: SimpleXMLElement::__construct(): ^ in /home/gopublic2014/public_html/piano3/wp-content/plugins/youtube-simplegallery/youtube_simplegallery.php on line 64
...

```

Line 64
```

		$videodata = new SimpleXMLElement($videodata);

```

I have been searching a while and found;
[RESOLVED] XML parsing problems
[http://www.webdeveloper.com/forum/showthread.php?222551-RESOLVED-XML-parsing-problems](http://www.webdeveloper.com/forum/showthread.php?222551-RESOLVED-XML-parsing-problems)

But I couldn't resolve it.  Please help.  Thanks

Regards
satimis

---

### Post by lisati on 2015-06-07
I had a quick look. This looks something that the owner of the website will have to address. 

Edit: Is this your website? It's possible that there are unmatched quotes or unmatched tags.

---

### Post by satimis on 2015-06-07
> **lisati said:**
> I had a quick look. This looks something that the owner of the website will have to address. 

Is this your website? It's possible that there are unmatched quotes or unmatched tags.
Hi,

Yes.  This is my website.

All websites managed by me with "youtube gallery plugin" having this problem.  It was discovered by me lately.  I don't know the cause?

satimis

---

### Post by satimis on 2015-06-08
Hi all,

Problem solved by comment out Line 64```

//      $videodata = new SimpleXMLElement($videodata);

```

Thanks

satimis

---

