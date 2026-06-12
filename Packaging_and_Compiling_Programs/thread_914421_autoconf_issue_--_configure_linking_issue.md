---
title: "autoconf issue -- configure linking issue"
date: 2008-09-08
forum: Packaging and Compiling Programs
---

### Post by audacity on 2008-09-08
Hi All, 
   maybe someone can help me understand some autoconf stuff I found in a ./configure file. Basically, it's a check for zlib, which fails. I can compile the example code just fine with -lz, but for some reason that's not being done with the script. Any ideas? 
The relevant section is as follows:
```
{ echo "$as_me:$LINENO: checking for deflate in -lz" >&5
echo $ECHO_N "checking for deflate in -lz... $ECHO_C" >&6; }
if test "${ac_cv_lib_z_deflate+set}" = set; then
  echo $ECHO_N "(cached) $ECHO_C" >&6
else
  ac_check_lib_save_LIBS=$LIBS
LIBS="-lz  $LIBS"
cat >conftest.$ac_ext <<_ACEOF
/* confdefs.h.  */
_ACEOF
cat confdefs.h >>conftest.$ac_ext
cat >>conftest.$ac_ext <<_ACEOF
/* end confdefs.h.  */

/* Override any GCC internal prototype to avoid an error.
   Use char because int might match the return type of a GCC
   builtin and then its argument prototype would still apply.  */
#ifdef __cplusplus
extern "C"
#endif
char deflate ();
#ifdef F77_DUMMY_MAIN

#  ifdef __cplusplus
     extern "C"
#  endif
   int F77_DUMMY_MAIN() { return 1; }

#endif
int
main ()
{
return deflate ();
  ;
  return 0;
}
_ACEOF
rm -f conftest.$ac_objext conftest$ac_exeext
if { (ac_try="$ac_link"
case "(($ac_try" in
  *\"* | *\`* | *\\*) ac_try_echo=\$ac_try;;
  *) ac_try_echo=$ac_try;;
esac
eval "echo \"\$as_me:$LINENO: $ac_try_echo\"") >&5
  (eval "$ac_link") 2>conftest.er1
  ac_status=$?
  grep -v '^ *+' conftest.er1 >conftest.err
  rm -f conftest.er1
  cat conftest.err >&5
  echo "$as_me:$LINENO: \$? = $ac_status" >&5
  (exit $ac_status); } && {
	 test -z "$ac_c_werror_flag" ||
	 test ! -s conftest.err
       } && test -s conftest$ac_exeext &&
       $as_test_x conftest$ac_exeext; then
  ac_cv_lib_z_deflate=yes
else
  echo "$as_me: failed program was:" >&5
sed 's/^/| /' conftest.$ac_ext >&5

	ac_cv_lib_z_deflate=no
fi

rm -f core conftest.err conftest.$ac_objext conftest_ipa8_conftest.oo \
      conftest$ac_exeext conftest.$ac_ext
LIBS=$ac_check_lib_save_LIBS
fi
{ echo "$as_me:$LINENO: result: $ac_cv_lib_z_deflate" >&5
echo "${ECHO_T}$ac_cv_lib_z_deflate" >&6; }
if test $ac_cv_lib_z_deflate = yes; then
  cat >>confdefs.h <<_ACEOF
#define HAVE_LIBZ 1
_ACEOF

  LIBS="-lz $LIBS"

else
  { echo "$as_me:$LINENO: WARNING: zlib is required for HDF5!" >&5
echo "$as_me: WARNING: zlib is required for HDF5!" >&2;}
fi

```

THANKS!

---

### Post by audacity on 2008-09-08
Hey, 
   So strangely enough, if I added the line --with-hdf5=/usr/lib (hdf5 was the package the check for zlib was needed for, was a prelim), problem disappears. So I'm still confused by the autoconf mess and would appreciate a walk-through (i.e. where does gcc get called?) but for now this mess is over.
Thanks

---

