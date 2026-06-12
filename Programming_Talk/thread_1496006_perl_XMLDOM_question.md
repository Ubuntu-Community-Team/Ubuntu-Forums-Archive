---
title: "perl XML::DOM question"
date: 2010-05-28
forum: Programming Talk
---

### Post by badperson on 2010-05-28
Hi,
What's the best way to open up an xml doc as a dom tree, make changes to the nodes, and then write the new changes to a different file? 

I'm trying to do something like:

```
my $doc = $parser->parsefile("parasWithEmph.xml");
## do stuff to tags...
print OUT $doc->printToFile('test.xml');

(where $doc is the document element);
```

---

