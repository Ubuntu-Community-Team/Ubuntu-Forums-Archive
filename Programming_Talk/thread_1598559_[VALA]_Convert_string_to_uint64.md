---
title: "[VALA] Convert string to uint64"
date: 2010-10-16
forum: Programming Talk
---

### Post by SpinningAround on 2010-10-16
I'm trying to convert a string to uint64 with the base 10, but haven't had any luck so far.

Method: [http://valadoc.org/glib-2.0/string.to_uint64.html](http://valadoc.org/glib-2.0/string.to_uint64.html)
```
public uint64 to_uint64 (out string endptr = null, int _base = 0) 
```

[PHP]
extern void exit(int exit_code);
public class Utility : GLib.Object{
	public static uint64[] read_traffic(string network){
		var file = File.new_for_path("/proc/net/dev");
		uint64[] values = new uint64[2];
		if( !file.query_exists(null) ){
			stderr.printf( "File '%s' doesn't exist.\n", file.get_path () );
			exit(-1);
		}
		string line=null, tok[] = null;
		try{
			int x=0;
			var in_stream = new DataInputStream( file.read (null) );
			while(x++<2 || (line = in_stream.read_line (null, null)) != null ){
				if(line.contains(network))
					break;
			}
		} catch(Error e){
			error("%s", e.message);
		}
		if(line==null){
			stderr.printf( "File '%s' don't contain %s exist.\n", file.get_path (), network );
			exit(-1);
		}
		line.replace(":"," ");
		tok = line.split("\\s+");
		values[0] = tok[2].to_int64(null,10);	// Fetch Download
		values[1] = tok[10].to_int64(null,10);	// Fetch Upload
		return values;
	}
}
[/PHP]

valac output
```

$ valac --pkg gio-2.0 -o utility utility.vala 
Vala/utility.vala.c: In function ‘utility_read_traffic’:
Vala/utility.vala.c:221: error: array size missing in ‘_tmp2_’
Vala/utility.vala.c:222: error: array size missing in ‘tok’
Vala/utility.vala.c:225: error: array size missing in ‘_tmp12_’
Vala/utility.vala.c:238: error: incompatible types when assigning to type ‘char *[1]’ from type ‘void *’
Vala/utility.vala.c:238: error: incompatible types when assigning to type ‘char *[1]’ from type ‘char **’
Vala/utility.vala.c:287: error: incompatible types when assigning to type ‘char *[1]’ from type ‘void *’
Vala/utility.vala.c:303: error: incompatible types when assigning to type ‘char *[1]’ from type ‘char **’
Vala/utility.vala.c:303: error: incompatible types when assigning to type ‘char *[1]’ from type ‘void *’
Vala/utility.vala.c:303: error: incompatible types when assigning to type ‘char *[1]’ from type ‘char **’
Vala/utility.vala.c:307: error: incompatible types when assigning to type ‘char *[1]’ from type ‘void *’
Vala/utility.vala.c:311: error: incompatible types when assigning to type ‘char *[1]’ from type ‘void *’
error: cc exited with status 256
Compilation failed: 1 error(s), 0 warning(s)


```

---

### Post by worksofcraft on 2010-10-16
> **SpinningAround said:**
> 
```

$ valac --pkg gio-2.0 -o utility utility.vala 
Vala/utility.vala.c: In function &#8216;utility_read_traffic&#8217;:

```

hum... I know nothing about valac, but your are telling the compiler that the function returns an array by value. When you do that, the compiler needs to know how big that array will be so it can allocate space (at compile time) to store it.

Instead you should return a pointer to the start of the array, which you can create dynamically using new. Then it doesn't matter how big the array will be. Similar in subsequent line, try it this way:

```

       uint64 *values = new uint64[2];

```

---

### Post by SpinningAround on 2010-10-17
Solved it, had nothing to do with uint64. Had simply declared tok the wrong way the correct way is 'string[] tok = null'

---

