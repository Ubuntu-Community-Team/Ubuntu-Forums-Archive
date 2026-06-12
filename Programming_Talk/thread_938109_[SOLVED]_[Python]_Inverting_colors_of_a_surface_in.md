---
title: "[SOLVED] [Python] Inverting colors of a surface in pygame?"
date: 2008-10-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-04
I got a pygame surface, and I want to inverse the colors of it. How?

---

### Post by crazyfuturamanoob on 2008-10-05
So I got only black and white on the surface. Can it be that hard to inverse the colors?

---

### Post by xlinuks on 2008-10-05
If you have access to pixels as numbers you can do that by hand using the xor operand. I don't know python, in Java it looks like this:
```

	public Main() {
		final int white = 0xFFFFFF;
		int x1 = 0xFFFFFF;
		int x2 = 0x000000;
		int x3 = 0x666666;
		int x4 = 0xEEEEEE;
		line( Integer.toHexString( x1 ) + ": " + Integer.toHexString((x1 ^ white)));
		line( Integer.toHexString( x2 ) + ": " + Integer.toHexString((x2 ^ white)));
		line( Integer.toHexString( x3 ) + ": "+ Integer.toHexString((x3 ^ white)));
		line( Integer.toHexString( x4 ) + ": "+ Integer.toHexString((x4 ^ white)));
	}
	
	public static final void line( Object obj ) {
		System.out.println( obj );
	}

```

It yields:
> 
ffffff: 0
0: ffffff
666666: 999999
eeeeee: 111111


---

### Post by crazyfuturamanoob on 2008-10-05
I found a workaround for the problem I needed color inversion, but thanks anyway.

---

