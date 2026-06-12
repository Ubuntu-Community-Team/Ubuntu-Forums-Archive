---
title: "ocaml - Can anyone see what my problem is?"
date: 2009-02-01
forum: Programming Talk
---

### Post by vandorjw on 2009-02-01
Some background. (I can provide more code if needed, just let me know)
Also, this is part of an assignment which is due Feb 3, 2009

I have an array full of object of type CircleT with is made up of 3 floats.
The array is of size 20.

```

let averageRadius()=
	if (!marker == 0) then raise EMPTY
	else
		let r_store = ref 0.0;
		for i = 0 to (!marker) do r_store := !r_store +. s.(i)#radius done;
		(!r_store /. float_of_int(!marker +1));;

```

All it tells me is "Syntax error" and puts ^^ under the last ';;'

Thanks for your help.

Cc7

---

### Post by vandorjw on 2009-02-02
```

let r_store = ref 0.0;

let averageRadius()=
	if (!marker == 0) then raise EMPTY
	else
		
		for i = 0 to (!marker) do r_store := !r_store +. s.(i)#radius done;
		(!r_store /. float_of_int(!marker +1));;

```


Problem is solved

---

