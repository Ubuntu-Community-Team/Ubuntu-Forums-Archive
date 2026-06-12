---
title: "Puzzling egrep behavior.  Possibly a bug?"
date: 2013-03-14
forum: Programming Talk
---

### Post by manthony121 on 2013-03-14
I am trying to extract a string from the output of a DICOM directory
parser.  The string I'm trying to match looks similar to this:

(0004,1500) CS #36 [DICOM\ST000000\SE000000\CR000000.DCM] Referenced File ID

"s" is a much larger string in which the target string is embedded.

From the console, this command produces no matches:
echo $s|egrep -o " \(0004,1500\) CS #[0-9]{2} \[.{,50}\] Referenced File ID "

However, any of these produce the expected result:
echo $s|egrep -o " \(0004,1500\) CS #[0-9]{2} \[.{,50}\] Reference. File ID "
echo $s|egrep -o " \(0004,1500\) CS #[0-9]{2} \[.{,50}\] Reference[d] File ID "
echo $s|egrep -o " \(0004,1500\) CS #[0-9]{2} \[.{1,50}\] Referenced File ID "

A typical output:
 (0004,1500) CS #36 [DICOM\ST000000\SE000000\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000000\SE000000\CR000001.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000000\SE000001\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000000\SE000002\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000000\SE000003\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000000\SE000004\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000000\SE000005\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000001\SE000000\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000001\SE000001\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000001\SE000002\CR000001.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000001\SE000002\CR000000.DCM] Referenced File ID 
 (0004,1500) CS #36 [DICOM\ST000001\SE000003\CR000000.DCM] Referenced File ID 


In summary, if I use the form, ".{,40}" to specify the variable part of
the string, egrep won't recognize a match between "Referenced" and
"Referenced", but will recognize "Reference." and "Reference[d]".  If I
use ".{1,40}", then "Referenced" matches "Referenced", as expected.

This would seem to be a bug, unless there is something about the regular
expression that I'm missing.

I'm using GNU bash, version 4.1.5(1), and GNU grep, version 2.5.4
OS: Ubuntu 10.04.4 LTS

Any advice would be appreciated.

manthony121

---

### Post by schragge on 2013-03-14
Hmm, [COLOR=#0000FF]{,n}[/COLOR] interval is obviously GNU egrep-specific. The POSIX standard defines only [COLOR=#0000ff]{m}[/COLOR], [COLOR=#0000ff]{m,n}[/COLOR] and [COLOR=#0000ff]{m,}[/COLOR]. Interestingly, even GNU grep treats [COLOR=#0000FF]\{,n\}[/COLOR] as an error.

Looks like a bug in egrep. Compare the output of
```

echo x|egrep -o 'x?'
echo x|egrep -o 'x{0,1}'
echo x|egrep -o 'x{,1}'
echo 'x{,1}'|egrep -o 'x{,1}'

```
The third form finds no match, but the fourth matches x.

[highlight]Update.[/highlight]
The above was tested  with cygwin grep on Windows. Now, on Debian with grep 2.12-2 / libc6 2.13-38 all examples above match x. I guess it was fixed in glibc at some point.

---

### Post by papibe on 2013-03-14
Hi manthony121.

The expression:
```
\[ \]
```
is not having the effect you want, then this:
```
.{,50}
```
is matching anything up to 50 chars, which happens to be up to "...Reference".

If you replace it with the following expression, it should work:
```
[[] []]
```

Try this:
```
egrep  "\(0004,1500\) CS #[0-9]{2} **[COLOR="#FF0000"][[][/COLOR]**.{,50}[COLOR="#FF0000"]**[]]**[/COLOR] Referenced File ID"  yourfile.txt
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by manthony121 on 2013-03-14
schragge:  thank you for the reply.  I didn't know that the {,m} form was non-standard.  The man page lists it as acceptable.

papibe: The expression as you wrote it works perfectly.  On re-reading the man page, I realized that nowhere does it specify that you can include a literal '[' in a string by preceding it with a backslash, as I had assumed.  The only place that specifies how to include a literal '[' is in the section on bracket expressions, where, as you point out, you can specify a literal '[' by placing it first within a bracket expression.

Thank you for showing how to write the regex properly.

However, it still seems to be buggy behavior.  The expression fails on the "d" in "Referenced" regardless of the number included in the ".{,50}" expression, and, changing ".{,50}" to ".{1,50}" results in the behavior that would be expected if "\[" were equivalent to "[[]".

As I play with it some more, it does seem to be a problem with the ".{,50}" idiom.  Eliminating the square brackets completely does not affect the result:

egrep -o " \(0004,1500\) CS #[0-9]{2} .{,80} Referenced File ID " doesn't match.
egrep -o " \(0004,1500\) CS #[0-9]{2} .{1,80} Referenced File ID " does match.
egrep -o " \(0004,1500\) CS #[0-9]{2} .{,80} Reference. File ID " also matches.

I think the moral of the story is to avoid the "{,m}" idiom!

Thanks again.

---

### Post by papibe on 2013-03-14
> **manthony121 said:**
> I think the moral of the story is to avoid the "{,m}" idiom!
I think you are right.

That option is no longer documented (and I guess not supported) on grep 2.10 (Ubuntu 12.04).

Regards.

EDIT: don't get me wrong, these are still supported:
```
      {n}     The preceding item is matched exactly n times.
      {n,}    The preceding item is matched n or more times.
      {n,m}   The  preceding  item  is  matched at least n times, but not more
              than m times.
```

---

### Post by schragge on 2013-03-15
> **manthony121 said:**
> On re-reading the man page, I realized that nowhere does it specify that you can include a literal '[' in a string by preceding it with a backslash, as I had assumed.Actually, your assumption is a reasonable one. At least, this is how I read [the standard](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap09.html#tag_09_04) (specifically, 9.4.1-9.4.3). This is also how the implementations I tested work, i.e. libc6 2.13, libpcre 8.30, and grep/egrep in Solaris 8.

---

### Post by manthony121 on 2013-03-15
It seems that "\[" does have the desired effect of matching a literal "[".  However, when used with the cursed ".{,50}" construct, it does not behave quite the same way as "[[]".  So, I will use both "[[]" and avoid ".{,m} in my future regexes.

---

