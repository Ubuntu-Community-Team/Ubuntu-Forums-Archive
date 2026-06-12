---
title: "Can I delete .pyc files safely?"
date: 2007-09-12
forum: Programming Talk
---

### Post by trishacupra on 2007-09-12
Is it okay to delete .pyc files in my filesystem? Thanks.

---

### Post by loell on 2007-09-12
generally the answer is yes :)

---

### Post by bashologist on 2007-09-12
If they appear after you execute something. You shouldn't go around your system deleting random pyc files tho. They're generally used to save time, so if you're debugging a python application it might be a good idea to save them until you're done.

---

### Post by pmasiar on 2007-09-12
.pyc is compiled Python source. You can delete it if you have sources, Python will compile new ones as needed. But sometimes ppl distribute .pyc instead of .py sources, and if you delete them, you may have problem :-)

---

### Post by trishacupra on 2007-09-12
Great, thanks. I was using Kleansweep and it suggested deleting pyc files, but I wasn't sure what they were. :)

---

