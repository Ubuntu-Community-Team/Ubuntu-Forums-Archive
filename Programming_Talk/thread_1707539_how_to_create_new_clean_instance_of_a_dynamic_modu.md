---
title: "how to create new clean instance of a dynamic module with GModule"
date: 2011-03-15
forum: Programming Talk
---

### Post by derlinuxer on 2011-03-15
Hi,

I've a module/plugin which can run with different configuration settings and it will have some static stuff and timer inside.
So I'll start the module with different parameter but if I load the module to create the next instance the static values are set of the first instance.
How can I init a instance of a module which is complete independent of another instance of the same module.

I try to do this with gmodule in C

The single instance is running well.

thanks

derlinuxer

---

### Post by derlinuxer on 2011-03-15
For better understanding a code example which shows my issue:
(without any any checks and mem frees)

module:
```
G_MODULE_EXPORT  
void sberg_test (void)
{
	static gchar *in_func = NULL;
	
	if (!in_func)
	{
		in_func = g_strdup("Hello");
		g_print("Set var!: %s\n", in_func);
	}
	else
	{
		g_print("Var already set!: %s\n", in_func);
	}
}

```

the loader:
```
void test_open_multi(void)
{
	GModule *module, *module1;
	gchar *module_full = NULL;

	typedef void (*TEST) (void);

	TEST test_func;
	TEST test_func_1;

	module_full = g_strconcat(MOD_PATH, "lookup_evolution.so", NULL);

	module = g_module_open (module_full, G_MODULE_BIND_LAZY);	
	g_module_symbol (module, "sberg_test", (gpointer*)&test_func);
	g_print ("first run\n");
	test_func();

	module1 = g_module_open (module_full, G_MODULE_BIND_LAZY);
	g_module_symbol (module1, "sberg_test", (gpointer*)&test_func_1);
	g_print ("second run\n");
	test_func_1();
}
```

and the output:

```
first run
Set var!: Hello
second run
Var already set!: Hello
```

So the first run will set the var and second found the static var.

---

### Post by derlinuxer on 2011-03-29
Hi,

found some answers at [Stackoverflow Forum]("http://stackoverflow.com"). So it's generally possible but it's not very common to do this. So I decided to redesign my module (shared Lib) that it can handle multiple instances by it self.

Thanks for reading ;)

derlinuxer

---

