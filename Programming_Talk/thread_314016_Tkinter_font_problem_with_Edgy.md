---
title: "Tkinter font problem with Edgy"
date: 2006-12-06
forum: Programming Talk
---

### Post by abovett on 2006-12-06
Hi

Having some problems with a Python/Tkinter program under Edgy. Under Dapper, this works:
```
        self.font = tkFont.Font( family="Bitstream Vera Sans",
                                 size=48,
                                 weight=tkFont.BOLD,
                                 slant=tkFont.ITALIC )
```
but under Edgy it dosn't (I get a default - serif'd - font).

Anyone know why?

I noticed that **xlsfonts | grep -i vera** does not return anything under Edgy but does under Dapper - is this connected?

Cheers

Andy B

---

### Post by dwblas on 2006-12-08
The first pass would suggest that you don't have it installed.  Use Synaptic to search for ttf-bitstream-vera and see if it is installled.  I think that's what you want, but not really sure.

---

### Post by abovett on 2006-12-09
> **dwblas said:**
> The first pass would suggest that you don't have it installed.
Thanks, but no - it's installed:
```
[andrew@jupiter ~]$ aptitude search ttf-bitstream-vera
i   ttf-bitstream-vera              - The Bitstream Vera family of free TrueType

```Other programs (e.g. OpenOffice) can access it OK. Any other ideas?

---

### Post by abovett on 2006-12-19
*bump*

---

### Post by dwblas on 2006-12-22
You have to have xfs installed to use a truetype font.  See if Synaptic says that it is installed.

---

