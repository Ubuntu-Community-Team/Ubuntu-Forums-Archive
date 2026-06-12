---
title: "Why so many MOVs in my compiled code with GCC?"
date: 2009-02-07
forum: Programming Talk
---

### Post by tom66 on 2009-02-07
I am wondering why my function has so many MOVs near the end of it when disassembled when it is a relatively simple function.

Compare:
```

08048c8c <shape_pop_transformation_stack>:
 8048c8c:	55                   	push   %ebp
 8048c8d:	89 e5                	mov    %esp,%ebp
 8048c8f:	83 ec 18             	sub    $0x18,%esp
 8048c92:	8b 45 08             	mov    0x8(%ebp),%eax
 8048c95:	8b 40 4c             	mov    0x4c(%eax),%eax
 8048c98:	83 e8 01             	sub    $0x1,%eax
 8048c9b:	c1 e0 02             	shl    $0x2,%eax
 8048c9e:	89 c2                	mov    %eax,%edx
 8048ca0:	8b 45 08             	mov    0x8(%ebp),%eax
 8048ca3:	8b 40 48             	mov    0x48(%eax),%eax
 8048ca6:	89 54 24 04          	mov    %edx,0x4(%esp)
 8048caa:	89 04 24             	mov    %eax,(%esp)
 8048cad:	e8 de fb ff ff       	call   8048890 <realloc@plt>
 8048cb2:	89 c2                	mov    %eax,%edx
 8048cb4:	8b 45 08             	mov    0x8(%ebp),%eax
 8048cb7:	89 50 48             	mov    %edx,0x48(%eax)
 8048cba:	8b 45 08             	mov    0x8(%ebp),%eax
 8048cbd:	8b 40 48             	mov    0x48(%eax),%eax
 8048cc0:	85 c0                	test   %eax,%eax
 8048cc2:	75 24                	jne    8048ce8 <shape_pop_transformation_stack+0x5c>
 8048cc4:	c7 44 24 0c b0 95 04 	movl   $0x80495b0,0xc(%esp)
 8048ccb:	08 
 8048ccc:	c7 44 24 08 4e 00 00 	movl   $0x4e,0x8(%esp)
 8048cd3:	00 
 8048cd4:	c7 44 24 04 f0 94 04 	movl   $0x80494f0,0x4(%esp)
 8048cdb:	08 
 8048cdc:	c7 04 24 cf 95 04 08 	movl   $0x80495cf,(%esp)
 8048ce3:	e8 e8 fb ff ff       	call   80488d0 <__assert_fail@plt>
 8048ce8:	8b 45 08             	mov    0x8(%ebp),%eax
 8048ceb:	8b 40 4c             	mov    0x4c(%eax),%eax
 8048cee:	85 c0                	test   %eax,%eax
 8048cf0:	7f 24                	jg     8048d16 <shape_pop_transformation_stack+0x8a>
 8048cf2:	c7 44 24 0c b0 95 04 	movl   $0x80495b0,0xc(%esp)
 8048cf9:	08 
 8048cfa:	c7 44 24 08 4f 00 00 	movl   $0x4f,0x8(%esp)
 8048d01:	00 
 8048d02:	c7 44 24 04 f0 94 04 	movl   $0x80494f0,0x4(%esp)
 8048d09:	08 
 8048d0a:	c7 04 24 ed 95 04 08 	movl   $0x80495ed,(%esp)
 8048d11:	e8 ba fb ff ff       	call   80488d0 <__assert_fail@plt>
 8048d16:	8b 45 08             	mov    0x8(%ebp),%eax
 8048d19:	8b 48 48             	mov    0x48(%eax),%ecx
 8048d1c:	8b 45 08             	mov    0x8(%ebp),%eax
 8048d1f:	8b 40 4c             	mov    0x4c(%eax),%eax
 8048d22:	89 c2                	mov    %eax,%edx
 8048d24:	89 d0                	mov    %edx,%eax
 8048d26:	01 c0                	add    %eax,%eax
 8048d28:	01 d0                	add    %edx,%eax
 8048d2a:	c1 e0 04             	shl    $0x4,%eax
 8048d2d:	8d 14 01             	lea    (%ecx,%eax,1),%edx
 8048d30:	8b 4d 0c             	mov    0xc(%ebp),%ecx
 8048d33:	8b 02                	mov    (%edx),%eax
 8048d35:	89 01                	mov    %eax,(%ecx)
 8048d37:	8b 42 04             	mov    0x4(%edx),%eax
 8048d3a:	89 41 04             	mov    %eax,0x4(%ecx)
 8048d3d:	8b 42 08             	mov    0x8(%edx),%eax
 8048d40:	89 41 08             	mov    %eax,0x8(%ecx)
 8048d43:	8b 42 0c             	mov    0xc(%edx),%eax
 8048d46:	89 41 0c             	mov    %eax,0xc(%ecx)
 8048d49:	8b 42 10             	mov    0x10(%edx),%eax
 8048d4c:	89 41 10             	mov    %eax,0x10(%ecx)
 8048d4f:	8b 42 14             	mov    0x14(%edx),%eax
 8048d52:	89 41 14             	mov    %eax,0x14(%ecx)
 8048d55:	8b 42 18             	mov    0x18(%edx),%eax
 8048d58:	89 41 18             	mov    %eax,0x18(%ecx)
 8048d5b:	8b 42 1c             	mov    0x1c(%edx),%eax
 8048d5e:	89 41 1c             	mov    %eax,0x1c(%ecx)
 8048d61:	8b 42 20             	mov    0x20(%edx),%eax
 8048d64:	89 41 20             	mov    %eax,0x20(%ecx)
 8048d67:	8b 42 24             	mov    0x24(%edx),%eax
 8048d6a:	89 41 24             	mov    %eax,0x24(%ecx)
 8048d6d:	8b 42 28             	mov    0x28(%edx),%eax
 8048d70:	89 41 28             	mov    %eax,0x28(%ecx)
 8048d73:	8b 42 2c             	mov    0x2c(%edx),%eax
 8048d76:	89 41 2c             	mov    %eax,0x2c(%ecx)
 8048d79:	8b 45 08             	mov    0x8(%ebp),%eax
 8048d7c:	8b 40 4c             	mov    0x4c(%eax),%eax
 8048d7f:	8d 50 ff             	lea    -0x1(%eax),%edx
 8048d82:	8b 45 08             	mov    0x8(%ebp),%eax
 8048d85:	89 50 4c             	mov    %edx,0x4c(%eax)
 8048d88:	c9                   	leave  
 8048d89:	c3                   	ret    

``` 

to:
```

/**
 * Pop an item from the transformation stack and put it in the *trans pointer.
 * @params	shape pointer, transformation pointer
 */
void shape_pop_transformation_stack(struct P_ShapeData *shape, struct P_ShapeTransform *trans)
{
    shape->trStack = realloc(shape->trStack, (shape->trSize - 1) * sizeof(struct P_ShapeTransform *));
    assert(shape->trStack != NULL);
    assert(shape->trSize > 0);
    *trans = shape->trStack[shape->trSize];
    shape->trSize--;
}

```

Why is this? Just a question, but it makes me think it's a bit inefficient with that. And this is without -O3; with -O3, a similar pattern appears, but it instead is in the middle of the routine.

---

### Post by jimi_hendrix on 2009-02-07
why shouldnt there be?

mov is the equal sign of asm (i assume you know that because you are reading a disassembled program so i assume you know asm)

so think of all the stuff it has to do that C is doing for you....

---

### Post by eye208 on 2009-02-07
> **tom66 said:**
> Why is this?
Because the last statement in your function copies an entire structure (= block of memory).

> Just a question, but it makes me think it's a bit inefficient with that.
You may think that a single MOV in a loop may be more efficient, but it's not, because the branch instruction takes additional CPU cycles.

Learn more about loop unwinding here: [http://en.wikipedia.org/wiki/Loop_unwinding](http://en.wikipedia.org/wiki/Loop_unwinding)

---

### Post by slavik on 2009-02-07
> **eye208 said:**
> Because the last statement in your function copies an entire structure (= block of memory).


You may think that a single MOV in a loop may be more efficient, but it's not, because the branch instruction takes additional CPU cycles.

Learn more about loop unwinding here: [http://en.wikipedia.org/wiki/Loop_unwinding](http://en.wikipedia.org/wiki/Loop_unwinding)
delayed branching has been know about for a long while now. ;)

---

### Post by eye208 on 2009-02-07
> **slavik said:**
> delayed branching has been know about for a long while now. ;)
Hmm, I'm not sure if delayed branching is related to loop unrolling. Then again, I haven't touched assembly language since the days of the ARM710...

---

### Post by wmcbrine on 2009-02-08
> **jimi_hendrix said:**
> mov is the equal sign of asmNicely put. :D

---

