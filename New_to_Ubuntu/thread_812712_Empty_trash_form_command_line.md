---
title: "Empty trash form command line?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-30
How can i empty trash form command line?

---

### Post by Delever on 2008-05-30
```

sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by sisco311 on 2008-05-30
```
rm -fr ~/.Trash/*
```

Hardy Heron(8.04):
```
rm -fr ~/.local/share/Trash/files/*
```

---

### Post by dje on 2008-05-30
You shouldn't need sudo permission
```
rm -rf ~/.local/share/Trash/files/*
```

dje

---

