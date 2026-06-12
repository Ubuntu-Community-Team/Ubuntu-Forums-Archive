---
title: "why &quot;if (0 &amp;&amp; foo)&quot;?"
date: 2007-12-14
forum: Programming Talk
---

### Post by jpkotta on 2007-12-14
I was reading some C code today, and I saw something like this:
```

if (0 && foo)
    bar(foo);

```

What is the point of the zero?  "foo" wasn't anything like a macro, if it didn't exist it would have been a compiler error (to be more precise, it looked more like foo->count, where count is an int).  I would be inclined to think the compiler would optimize out the "0 &&".  I looked around on the web a bit for an explanation, and found plenty of examples but no rational.  I am thoroughly confused.

---

### Post by LaRoza on 2007-12-14
> **jpkotta said:**
> I was reading some C code today, and I saw something like this:
```

if (0 && foo)
    bar(foo);

```

What is the point of the zero?  "foo" wasn't anything like a macro, if it didn't exist it would have been a compiler error (to be more precise, it looked more like foo->count, where count is an int).  I would be inclined to think the compiler would optimize out the "0 &&".  I looked around on the web a bit for an explanation, and found plenty of examples but no rational.  I am thoroughly confused.

Some more of the C code would help.

I don't know why the 0 would be there, and a little more on what foo is is needed.

---

### Post by jpkotta on 2007-12-14
I am looking at ipkg, the Itsy Package Manager.  It's dpkg+apt for embedded systems.  You can get the full source from [http://www.handhelds.org/pub/packages/ipkg/](http://www.handhelds.org/pub/packages/ipkg/).

```

typedef struct pkg pkg_t;
struct pkg
{
     char *name;
     unsigned long epoch;
     char *version;
     char *revision;
     char *familiar_revision;
     pkg_src_t *src;
     pkg_dest_t *dest;
     char *architecture;
     char *section;
     char *maintainer;
     char *description;
     pkg_state_want_t state_want;
     pkg_state_flag_t state_flag;
     pkg_state_status_t state_status;
     char **depends_str;
     int depends_count;
     char **pre_depends_str;
     int pre_depends_count;
     char **recommends_str;
     int recommends_count;
     char **suggests_str;
     int suggests_count;
     compound_depend_t * depends;

     /* Abhaya: new conflicts */
     char **conflicts_str;
     compound_depend_t * conflicts;
     int conflicts_count;
	
     char **replaces_str;
     int replaces_count;
     abstract_pkg_t ** replaces;

     char **provides_str;
     int provides_count;
     abstract_pkg_t ** provides;

     abstract_pkg_t *parent;

     pkg_t *old_pkg; /* during upgrade, points from installee to previously installed */

     char *filename;
     char *local_filename;
     char *url;
     char *tmp_unpack_dir;
     char *md5sum;
     char *size;
     char *installed_size;
     char *priority;
     char *source;
     conffile_list_t conffiles;
     time_t installed_time;
     /* As pointer for lazy evaluation */
     str_list_t *installed_files;
     /* XXX: CLEANUP: I'd like to perhaps come up with a better
	mechanism to avoid the problem here, (which is that the
	installed_files list was being freed from an inner loop while
	still being used within an outer loop. */
     int installed_files_ref_cnt;
     int essential;
     int arch_priority;
/* Adding this flag, to "force" ipkg to choose a "provided_by_hand" package, if there are multiple choice */
     int provided_by_hand;

     /* Check whether this pkg is being removed or installed */
     int is_processing;
     
};
```

```

int buildDepends(hash_table_t * hash, pkg_t * pkg)
{
     int count;
     register int i;
     compound_depend_t * depends;

     if(!(count = pkg->pre_depends_count + pkg->depends_count + pkg->recommends_count + pkg->suggests_count))
	  return 0;

     if (0 && pkg->pre_depends_count)
	  fprintf(stderr, "pkg=%s pre_depends_count=%d depends_count=%d\n", 
		  pkg->name, pkg->pre_depends_count, pkg->depends_count);
     depends = pkg->depends = malloc(sizeof(compound_depend_t) * count);
     if (depends == NULL) {
        fprintf(stderr, "%s: out of memory\n", __FUNCTION__);
        return  -1;
     }

...

```

---

### Post by kzutter on 2007-12-14
I think it is to get the side effects of foo

---

### Post by engla on 2007-12-14
The short-circuiting rules of C would make sure foo is never evalutated, and the if clause is never entered since the expression is never true. This must be a "lazy"/temporary comment-out of the following if-block, akin to the thing more often seen in preprocessor:

```
#if 0
things here effectively commented out
..
#endif
```

---

### Post by Auria on 2007-12-14
> 
I think it is to get the side effects of foo


no, because foo is never called. the only thing i can think of is that it is to disable that line (but then why didn't the author use comments?) anyway maybe if you asked the author he wouldn't know himself, we all find weirdness in our own code sometimes ;)

---

### Post by Wybiral on 2007-12-14
As engla said, sometimes programmers do that during debugging as a "switch" to turn a certain block of code off. Typically they use macros because conditions will still be processed (unless the compiler optimizes it out). But it's likely to just be a toggle switch for that functionality.

---

### Post by rplantz on 2007-12-14
> **Auria said:**
> ...anyway maybe if you asked the author he wouldn't know himself, we all find weirdness in our own code sometimes ;)

This assumes that the author can remember why he/she did it.:confused:

Yet another reason to comment one's code.

---

### Post by jpkotta on 2007-12-14
OK, that makes sense.  It's probably an error if predepends_count is zero, and the only thing inside the if() is a debug print.  They probably guarantee that it is always nonzero (I remember seeing elsewhere in the code something about a package always depending on itself), thus the check is not useful in normal operation and only for testing.  There are similar checks for a number of other counts in pkg.  Thanks for the insight.

And an #ifdef TESTING would have been better.

---

### Post by rplantz on 2007-12-15
This could also be a typo. Perhaps the author meant to write
```

if (0 == pkg->pre_depends_count)

```

I taught CS for over twenty years. I refused to grade programming assignments that did not have comments. That came from working in industry for several years before going into teaching. I had to read other people's code (and my own code a few weeks after I wrote it).

---

### Post by Wybiral on 2007-12-15
I agree, the lack of commenting in this code is horrendous (especially if you're going to use odd tricks like that).

---

### Post by Majorix on 2007-12-15
> **jpkotta said:**
> I was reading some C code today, and I saw something like this:
```

if (0 && foo)
    bar(foo);

```

What is the point of the zero?  "foo" wasn't anything like a macro, if it didn't exist it would have been a compiler error (to be more precise, it looked more like foo->count, where count is an int).  I would be inclined to think the compiler would optimize out the "0 &&".  I looked around on the web a bit for an explanation, and found plenty of examples but no rational.  I am thoroughly confused.

We all realize that this program won't execute the if-block right? Because since 0 is false in C and C++, no matter what the value of foo would be (I cannot say what its value is or anything since you only partially quoted the code) the condition will be "false".

---

### Post by LaRoza on 2007-12-15
> **Majorix said:**
> We all realize that this program won't execute the if-block right? Because since 0 is false in C and C++, no matter what the value of foo would be (I cannot say what its value is or anything since you only partially quoted the code) the condition will be "false".

That was established, it is believed to be a way to block code from executing, instead of commenting it out.

---

### Post by Majorix on 2007-12-15
OK sorry for interrupting then :KS

---

