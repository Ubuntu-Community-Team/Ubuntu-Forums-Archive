---
title: "sed help"
date: 2010-07-23
forum: Programming Talk
---

### Post by AstroLlama on 2010-07-23
I've been playing around with sed, can somebody help figure this out?

I want to remove all text in an xml file between two <caption> tags. I've used the following command:
```

sed 's/<caption>[A-Za-z]*<\/caption>/<caption><\/caption>/g' file.xml >file2.xml

```

This works, but only if there is one word between the tags. I've tried modifying the command to remove multiple words in various ways but to no success. any sed gurus out there have advice?

---

### Post by imbjr on 2010-07-23
> **AstroLlama said:**
> I've been playing around with sed, can somebody help figure this out?

I want to remove all text in an xml file between two <caption> tags. I've used the following command:
```

sed 's/<caption>[A-Za-z]*<\/caption>/<caption><\/caption>/g' file.xml >file2.xml

```

This works, but only if there is one word between the tags. I've tried modifying the command to remove multiple words in various ways but to no success. any sed gurus out there have advice?

I think you might need a space in that A-Za-z part of the clause:

```

sed 's/<caption>[A-Z a-z]*<\/caption>/<caption><\/caption>/g' file.xml >file2.xml

```

---

### Post by DaithiF on 2010-07-23
Hi,
another possibility would be:
```
sed 's/<caption>[^<]*<\/caption>/<caption><\/caption>/g'

```
which will handle cases where there are punctuation or other non-alphabetic characters in the caption tags

---

### Post by mobilediesel on 2010-07-23
> **AstroLlama said:**
> I've been playing around with sed, can somebody help figure this out?

I want to remove all text in an xml file between two <caption> tags. I've used the following command:
```

sed 's/<caption>[A-Za-z]*<\/caption>/<caption><\/caption>/g' file.xml >file2.xml

```

This works, but only if there is one word between the tags. I've tried modifying the command to remove multiple words in various ways but to no success. any sed gurus out there have advice?

This works, too, and shortens the command a bit:
```
sed 's/\(<caption>\)[^<]*\(<\/caption>\)/\1\2/g' file.xml >file2.xml
```

Using **[^<]*** will match any character up to the **</caption>** tag. Putting **<caption>** and **<\/caption>** inside **(** and **)** means you only need **\1\2** in the replacement end.

---

### Post by mobilediesel on 2010-07-23
> **DaithiF said:**
> Hi,
another possibility would be:
```
sed 's/<caption>[^<]*<\/caption>/<caption><\/caption>/g'

```
which will handle cases where there are punctuation or other non-alphabetic characters in the caption tags

Ah! I had the preview open while I went off and did something else and come back and someone posts what I had!

I should start refreshing the post again before hitting submit. :D

*AND I should start editing my post so as not to post twice in a row...*

---

### Post by howlingmadhowie on 2010-07-23
> **mobilediesel said:**
> This works, too, and shortens the command a bit:
```
sed 's/\(<caption>\)[^<]*\(<\/caption>\)/\1\2/g' file.xml >file2.xml
```

Using **[^<]*** will match any character up to the **</caption>** tag. Putting **<caption>** and **<\/caption>** inside **(** and **)** means you only need **\1\2** in the replacement end.

one thing worth noting is that the command separator for sed doesn't have to be a '/', so you could instead write it like this:
```

sed 's:\(<caption\)[^<]*\(</caption>\):\1\2:g' file.xml > file2.xml

```
which is a bit more legible

---

### Post by mobilediesel on 2010-07-23
> **howlingmadhowie said:**
> one thing worth noting is that the command separator for sed doesn't have to be a '/', so you could instead write it like this:
```

sed 's:\(<caption\)[^<]*\(</caption>\):\1\2:g' file.xml > file2.xml

```
which is a bit more legible

I keep forgetting that for some reason. There are plenty of instances where using different separators make sed WAY easier to work with.

---

### Post by ghostdog74 on 2010-07-23
> **AstroLlama said:**
> I've been playing around with sed, can somebody help figure this out?

I want to remove all text in an xml file between two <caption> tags. I've used the following command:
```

sed 's/<caption>[A-Za-z]*<\/caption>/<caption><\/caption>/g' file.xml >file2.xml

```

This works, but only if there is one word between the tags. I've tried modifying the command to remove multiple words in various ways but to no success. any sed gurus out there have advice?


All the sed solutions provided thus far does not take care of multiline tags.
so why don't you ditch sed and use awk instead. 

```

# more file
<tag1>
  i want text here
  <tag2>
    remove text here
  </tag2>
  you want text here too
</tag1>

$ awk -vRS='</tag2>' '{ gsub(/<tag2>.*/,"")}1' file
<tag1>
  i want text here


  you want text here too
</tag1>



```

Best of all, use a proper XML parser if you can.

---

### Post by AstroLlama on 2010-07-23
thanks for the quick replies, studying these examples has proven to be a great lesson in how to use sed.

DaithiF
> **DaithiF said:**
> ```
sed 's/<caption>[^<]*<\/caption>/<caption><\/caption>/g'
```
which will handle cases where there are punctuation or other non-alphabetic characters in the caption tags

> **mobilediesel said:**
> This works, too, and shortens the command a bit:
```
sed 's/\(<caption>\)[^<]*\(<\/caption>\)/\1\2/g' file.xml >file2.xml
```

Using **[^<]*** will match any character up to the **</caption>** tag. Putting **<caption>** and **<\/caption>** inside **(** and **)** means you only need **\1\2** in the replacement end.

mobilediesel, though your command suggestion is slightly longer, the use of the parenthesis and numbers has other interesting applications that are sure to be helpful when doing more complicated sed work in the future.

thanks again!

---

