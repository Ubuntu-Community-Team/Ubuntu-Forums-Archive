---
title: "JTable column"
date: 2011-10-24
forum: Programming Talk
---

### Post by raac on 2011-10-24
I'm writing a java program and I was wondering if there is a way to restrict the columns of a table to move. I googled it, and I found I way to do it but not in a way that I would like.
 
The solution I found is when the user tries to drag the column, it will back to the original place once the user release the mouse button. What I want is to not let the user drag the column at all.
 
Thanks.

---

### Post by 11jmb on 2011-10-24
What is the way that you found on Google? You may be able to manhandle it a little bit by going through your columns with the getColumn method and then calling setResizeable for each column

---

### Post by ofnuts on 2011-10-24
> **raac said:**
> I'm writing a java program and I was wondering if there is a way to restrict the columns of a table to move. I googled it, and I found I way to do it but not in a way that I would like.
 
The solution I found is when the user tries to drag the column, it will back to the original place once the user release the mouse button. What I want is to not let the user drag the column at all.
 
Thanks.
```

[FONT=Book Antiqua][COLOR=Black][B][SIZE=1]theTable.getTableHeader().setReorderingAllowed(false)
[/SIZE][/B][/COLOR][/FONT]
```

---

### Post by raac on 2011-10-24
Thanks ofnuts, that is what I wanted. The google solution was implementing a listener for mouse drags.
 
Thanks again.

---

