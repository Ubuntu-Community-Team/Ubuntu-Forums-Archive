---
title: "Qthread+python"
date: 2008-05-23
forum: Programming Talk
---

### Post by tsic on 2008-05-23
Hello,
Is there any documentation or tutorial that help me in my client server program . (using python)
thank you

---

### Post by pmasiar on 2008-05-23
Did you read python.org docs? What exactly is your problem? And skill level? See wiki in my sig with links for beginners

---

### Post by Lau_of_DK on 2008-05-24
> **pmasiar said:**
> Did you read python.org docs? What exactly is your problem? And skill level? See wiki in my sig with links for beginners

Pmasiar,
(whats with the nick?)

I didnt really find any networking documentation following the link in your sig. Could you be more specific?

/Lau

---

### Post by tsic on 2008-05-24
Hello,
I'm not new with python,thanks for the link but it didn't help me a lot. I want a tutorial or a doxumentation to know the steps that I should fellow to use QThread with python.thank u

---

### Post by smartbei on 2008-05-24
Check this out for very basic usage:
```

import PyQt4.Qt as qt
import time
class MyThread(qt.QThread):
	def run(self):
		print "Entered Thread!"
		time.sleep(1)
		print "Exiting Thread!"

if __name__ == "__main__":
	m = MyThread()
	m.start()
	time.sleep(1.5)

```

---

