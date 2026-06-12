---
title: "glob.glob() not globbing"
date: 2010-02-17
forum: Programming Talk
---

### Post by abeisgreat on 2010-02-17
I have a directory with this path
```

/home/abeisgreat/Desktop/Code/Python[Desktop]/active/advr/video/

```
I call glob like this
```

glob.glob(os.path.join('/home/abeisgreat/Desktop/Code/Python[Desktop]/active/advr/video/', '*'))

```
It returns nothing, because of the [Desktop] part of the path, as you know [] are regex characters. And it's picking those up. I tried using re.escape, or just manually escaping those characters, but nothing seems to work properly.

Any help?

**Edit:**
I was able to work around this by doing:
```

os.chdir('/home/abeisgreat/Desktop/Code/Python[Desktop]/active/advr/video/')
glob.glob('*')

```
However, that is not horribly elegant. I'm still open to better solutions.

---

