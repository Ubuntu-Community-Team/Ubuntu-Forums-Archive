---
title: "Print out iframe code without printing object"
date: 2006-11-04
forum: Programming Talk
---

### Post by Super King on 2006-11-04
Figured I'd throw this out there: I'm writing a CGI script in Perl where I'd like to print out HTMl code for an iframe object without printing out the actual object itself. In this case the iframe is printing out a banner.

In my CGI script I've tried the following code, but the banner that the iframe makes shows up instead of the actual iframe code.

```
print "<iframe src='http://something.com' blah....></iframe>";
```

I also tried this, as <code> tags are supposed to ignore any code inbetween them, but it still prints out the banner.

```
print "**<code>**<iframe src='http://something.com' blah....></iframe>**</code>**";
```

Anyone have any suggestions?

---

