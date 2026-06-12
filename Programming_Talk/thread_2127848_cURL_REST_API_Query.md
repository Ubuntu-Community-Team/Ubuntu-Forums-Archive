---
title: "cURL REST API Query"
date: 2013-03-21
forum: Programming Talk
---

### Post by 3246251196 on 2013-03-21
I have not used cUrl before, but I have noticed that in my Perl script I give a query and it takes the format:

URL?query={*field*[**value**];*field*['**value**']}

But, when I try this with cUrl, it will not query at all:

*curl: (3) [globbing] nested braces not supported at pos 88*

I have tried moving the braces etc etc, it just does not seem to take the same format

So, the Perl works and it pulls back XML for the queried fields, but why will cUrl not accept this?

Thanks.

---

### Post by ofnuts on 2013-03-21
> **3246251196 said:**
> I have not used cUrl before, but I have noticed that in my Perl script I give a query and it takes the format:

URL?query={*field*[**value**];*field*['**value**']}

But, when I try this with cUrl, it will not query at all:

*curl: (3) [globbing] nested braces not supported at pos 88*

I have tried moving the braces etc etc, it just does not seem to take the same format

So, the Perl works and it pulls back XML for the queried fields, but why will cUrl not accept this?

Thanks.
May be the braces should be URL-escaped. Or more likely they are just an indication that the contents of "*field*[**value**];*field*['**value**']"  should be replaced by something adequate for the query, and they shouldn't be part of the final query.

---

