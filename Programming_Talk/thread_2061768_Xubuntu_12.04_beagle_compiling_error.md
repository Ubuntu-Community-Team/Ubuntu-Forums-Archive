---
title: "Xubuntu 12.04 beagle compiling error"
date: 2012-09-23
forum: Programming Talk
---

### Post by e_defranco on 2012-09-23
I am not a C programmer. I try to compile from source beagle for xubuntu 12.04 64bit (it is not in the repository).
I have the gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5).
When I compiling I get this error
mono-glue.c: In function ‘memory_usage’:
mono-glue.c:82:17: error: dereferencing pointer to incomplete type
mono-glue.c:89:27: error: dereferencing pointer to incomplete type
mono-glue.c:93:30: error: dereferencing pointer to incomplete type
on this code:

        int total = 0;
        MonoClass *klass;
        MonoType *type;
        gpointer iter = NULL;
        MonoClassField *field;

        if (g_hash_table_lookup (visited, obj))
                return 0;

        g_hash_table_insert (visited, obj, obj);

        klass = mono_object_get_class (obj);
        type = mono_class_get_type (klass);

        /* This is an array, so drill down into it */
row 82  if (type->type == MONO_TYPE_SZARRAY)
                total += memory_usage_array ((MonoArray *) obj, visited);

        while ((field = mono_class_get_fields (klass, &iter)) != NULL) {
                MonoType *ftype = mono_field_get_type (field);
                gpointer value;

row 89          if ((ftype->attrs & (FIELD_ATTRIBUTE_STATIC | FIELD_ATTRIBUTE_HAS_FIELD_RVA)) != 0)
                        continue;

                /* FIXME: There are probably other types we need to drill down into */
row 93                switch (ftype->type) {


I have undestand that the problem is linked to an uninitialized pointer, 
but I don't know how to fix.
There are some person that can help me ?
Thank in advance,
Emilio

---

### Post by cariboo on 2012-09-23
You'll probably get an answer quicker here, than in a forum devoted to creating new Ubuntu programs.

---

### Post by directhex on 2012-09-24
Beagle is a very, very, very dead project. It no longer builds AFAIK.

---

