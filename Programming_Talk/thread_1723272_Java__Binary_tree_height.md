---
title: "Java : Binary tree height"
date: 2011-04-06
forum: Programming Talk
---

### Post by Quake on 2011-04-06
I was trying to write a binary tree height using a recursive method... but I just couldn't figure it out. Then after looking around I saw that Math.max (leftbranch, rightbranch) can do the trick.

The thing is, I don't know if my prof will accept this solution. Is it difficult to implement it? Note that this is a Java II first year university.

Thanks.

---

### Post by Some Penguin on 2011-04-06
Unless your professor is evil enough to check with trees so deep that they'll overflow your process's stack space (and that's unlikely if recursion was specified), he'll be looking for the simple and elegant answer.

---

### Post by Simian Man on 2011-04-06
The height at any node is equal to 1 + the height of whichever of its children has the greatest height.  That's all you'll get.

---

### Post by NovaAesa on 2011-04-06
> **Quake said:**
> The thing is, I don't know if my prof will accept this solution. Is it difficult to implement it?

Why wouldn't he/she accept a recursive solution? In Java, the maximum stack size can be arbitrarily adjusted, so that really shouldn't be an issue.

For me at least, it's much easier to get my head around recursive solutions compared to iterative solutions when it comes to trees. It should be easy to implement, about 10 lines of code maximum.

---

### Post by Quake on 2011-04-06
> **NovaAesa said:**
> Why wouldn't he/she accept a recursive solution? In Java, the maximum stack size can be arbitrarily adjusted, so that really shouldn't be an issue.

Nah, it has to be recursive, I just thought it would be extremely hard.

This is what I came up with:

> 
if ( node == null) {
return -1;
}
else {
int left = height(node.left);
int right = height(node.right);
...

I'm not going to post the whole code as I'm afraid one of my classmates will copy it (Yes, I'm paranoid).

It works... but I need to understand something.. will it check every nodes until the base case is reached?

---

### Post by simeon87 on 2011-04-07
> **Quake said:**
> Nah, it has to be recursive, I just thought it would be extremely hard.

This is what I came up with:


I'm not going to post the whole code as I'm afraid one of my classmates will copy it (Yes, I'm paranoid).

It works... but I need to understand something.. will it check every nodes until the base case is reached?

We can't answer that question as you haven't shown us the recursive calls. But if you make sure that, for each node, you recursively look at the left subtree and the right subtree then your approach should indeed see all nodes. If it's an ordinary binary tree then the only base case is when a node is null as that indicates you have reached a leaf node.

---

### Post by chaoprokia on 2011-04-07
> **Quake said:**
> Nah, it has to be recursive, I just thought it would be extremely hard.
 
This is what I came up with:
 
 
I'm not going to post the whole code as I'm afraid one of my classmates will copy it (Yes, I'm paranoid).
 
It works... but I need to understand something.. will it check every nodes until the base case is reached?
 
well after u return it most likely the code below is compare left and right and return the highest value.
That is correct to calculate height.
the 2nd way is u can use Queue to help u calculate height

---

### Post by Some Penguin on 2011-04-07
> **Quake said:**
> Nah, it has to be recursive, I just thought it would be extremely hard.

This is what I came up with:


I'm not going to post the whole code as I'm afraid one of my classmates will copy it (Yes, I'm paranoid).

It works... but I need to understand something.. will it check every nodes until the base case is reached?

Try a proof by induction.

---

