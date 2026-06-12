---
title: "Find text"
date: 2009-12-21
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-12-21
What's Up?

OK, So as one project gets finished, Another one starts! Although this one should be more easier. Basically i need to be able to search a file for some text, Now the text i want will be differ from time to time, But its always in a specific spot. I'm trying to grab it from a .html file.

```
<dt>Interests:</dt> <dd>_Text i want to grab here_</dd><dt>Groups
```

So the text i want is always going to be, in between those html tags, How'd you think i could take the text from their?

Thanks Bye!

---

### Post by Barriehie on 2009-12-21
> **Chamillionaire2 said:**
> What's Up?

OK, So as one project gets finished, Another one starts! Although this one should be more easier. Basically i need to be able to search a file for some text, Now the text i want will be differ from time to time, But its always in a specific spot. I'm trying to grab it from a .html file.

```
<dt>Interests:</dt> <dd>_Text i want to grab here_</dd><dt>Groups
```

So the text i want is always going to be, in between those html tags, How'd you think i could take the text from their?

Thanks Bye!

I'm a beginner with regexpr but this will print out the line.  I'm sure some more astute members can come up with an awk routine that can one up this.  My awk routine isn't working...

```

grep [$????Interests.*Groups^] ./testfile
```

Barrie

---

### Post by Chamillionaire2 on 2009-12-21
> **Barriehie said:**
> I'm a beginner with regexpr but this will print out the line.  I'm sure some more astute members can come up with an awk routine that can one up this.  My awk routine isn't working...

```

grep [$????Interests.*Groups^] ./testfile
```

Barrie

I tried your script but it just prints the entire source code of the file, Not just whats in between thoses tags.

---

### Post by benj1 on 2009-12-21
assuming its the <dd> tags
```
sed -n 's/.*<dd>\([^<]*\)<\/dd>.*/\1/p'
```

---

### Post by Barriehie on 2009-12-21
> **Chamillionaire2 said:**
> I tried your script but it just prints the entire source code of the file, Not just whats in between thoses tags.

Ooops, how about posting the file to be processed?

Barrie

---

### Post by ghostdog74 on 2009-12-21
```

awk -vRS="</dd>" '/<dd>/{gsub(/.*<dd>/,"");print}' file

```

---

### Post by ghostdog74 on 2009-12-21
> **benj1 said:**
> assuming its the <dd> tags
```
sed -n 's/.*<dd>\([^<]*\)<\/dd>.*/\1/p'
```
what if more than a pair of dd's are on one line?

---

### Post by diesch on 2009-12-21
```
echo 'xpath //dd/text()'|xmllint -html --shell YOUR_FILE.html|awk -F= '/^ *content=/ {print $2}'
```

*xmllint* is in package *libxml2-utils*

---

