---
title: "some strange errors while compiling bison and flex..."
date: 2011-03-20
forum: Programming Talk
---

### Post by ynj on 2011-03-20
I'm a freshman in bison and flex. I meet some problem while compiling. Here is the situation of my errors.
ynj@ynj-VirtualBox:~$ flex a.lex
ynj@ynj-VirtualBox:~$ bison -d a.y
ynj@ynj-VirtualBox:~$ cc  a.tab.c lex.yy.c -ly -lfl
a.tab.c:293: warning: declaration does not declare anything
a.tab.c:293: error: expected specifier-qualifier-list before ‘yyvs_alloc’
a.tab.c:996: error: expected declaration specifiers or ‘...’ before ‘*’ token
a.tab.c: In function ‘yydestruct’:
a.tab.c:1005: error: ‘yyvaluep’ undeclared (first use in this function)
a.tab.c:1005: error: (Each undeclared identifier is reported only once
a.tab.c:1005: error: for each function it appears in.)
a.tab.c:1007: error: ‘yymsg’ undeclared (first use in this function)
a.tab.c:1011: error: ‘yytype’ undeclared (first use in this function)
a.tab.c: At top level:
a.tab.c:1039: warning: useless type name in empty declaration
a.tab.c:1039: warning: data definition has no type or storage class
a.tab.c: In function ‘yyparse’:
a.tab.c:1091: warning: useless type name in empty declaration
a.tab.c:1091: error: ‘yyvsa’ undeclared (first use in this function)
a.tab.c:1092: warning: useless type name in empty declaration
a.tab.c:1092: error: ‘yyvs’ undeclared (first use in this function)
a.tab.c:1093: warning: useless type name in empty declaration
a.tab.c:1093: error: ‘yyvsp’ undeclared (first use in this function)
a.tab.c:1103: warning: useless type name in empty declaration
a.tab.c:1103: error: ‘yyval’ undeclared (first use in this function)
a.tab.c:1189: error: expected ‘)’ before ‘;’ token
a.tab.c:1193: error: ‘union yyalloc’ has no member named ‘yyvs_alloc’
a.tab.c:1193: error: ‘union yyalloc’ has no member named ‘yyvs_alloc’
Here is my lex and y files. Can someone help me? Thanks a lot!!!

---

### Post by gmargo on 2011-03-20
In your yacc file, you have this line:
```

#define YYSTYPE int;

```The semi-colon does not belong.  Remove that and it compiles.

---

### Post by ynj on 2011-03-21
> **gmargo said:**
> In your yacc file, you have this line:
```

#define YYSTYPE int;

```The semi-colon does not belong.  Remove that and it compiles.
Great! Thanks a lot!

---

