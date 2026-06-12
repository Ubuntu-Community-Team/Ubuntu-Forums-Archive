---
title: "Shellscript"
date: 2012-04-14
forum: Programming Talk
---

### Post by Vishal Agarwal on 2012-04-14
Hi,

In the directory listing there are many files with blank spaces in name.

"My First Trip to US.pdf"

I want to change all these blank spaces with underscore character.

"My_First_Trip_to_US.pdf"

Pl help.

---

### Post by Vishal Agarwal on 2012-04-14
rename ~/pdffiles/"s/ */_/g" *.pdf

---

### Post by Vaphell on 2012-04-14
won't this put _ everywhere? ' *' matches any number of spaces **including 0**
use + (1-or-more) instead of *

```
$ touch "my trip whatever.pdf"
$ rename 's/ */_/g' *.pdf
$ ls
_m_y__t_r_i_p__w_h_a_t_e_v_e_r_._p_d_f_
```

---

### Post by mörgæs on 2012-04-14
Moved to Programming Talk.

---

### Post by TeoBigusGeekus on 2012-04-14
For cases like this I just use Thunar's Bulk Rename.

---

### Post by sisco311 on 2012-04-14
Perl rename:
```

rename -n 's/ /_/g' *\ *.pdf

```

Bash:
```

shopt -s nullglob
for file in *\ *.pdf
do
    mv -i -- "$file" "${file// /_}"
done
```

POSIX:
```

set -- *\ *.pdf

test -f "$1" || exit

for file
do
    new=$(printf '%s' "$file" | tr ' ' _)
    mv -i -- "$file" "$new"
done

```

---

### Post by Vishal Agarwal on 2012-04-15
Thanks a lot to every one.

---

