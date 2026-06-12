---
title: "understanding a.out files (assembler's output) -- their structure"
date: 2010-01-25
forum: Packaging and Compiling Programs
---

### Post by jzacsh on 2010-01-25
Hey, I'm new to programming (taking my second class on C++) and I love it.

[SIZE="3"]_Where I stand in knowledg_e[/SIZE]:
I've taken a course in assembly language (*we talked about Microsoft Assembler*). I'm reading [www.linuxfromscratch.org](www.linuxfromscratch.org) -- this lead me to: [http://www.tldp.org/HOWTO/Software-Building-HOWTO.html](http://www.tldp.org/HOWTO/Software-Building-HOWTO.html) and some of the stuff I'm reading is new to me.

[SIZE="3"]_Can you recommend reading on..._[/SIZE]
So now that article's talk about ELF vs a.out file formats got me thinking about -- what exactly is in those files? Is it really all zeros and ones and just wouldn't look like anything to me? *Can't be, because then where would strings I type in `cout' statements go?*?

[SIZE="3"]_I tried:_[/SIZE]
```

**$** echo '#include<iostream>
using namespace std;

int main(){
cout << "Hello world" << endl;
} ' > ./sample.cpp
**$** g++ ./sample.cpp
**$** less ./a.out | strings | less
"./a.out" may be a binary file.  See it anyway? y
[I]
/lib/ld-linux.so.2
_UR[y=
CyIk
libstdc++.so.6
__gmon_start__
_Jv_RegisterClasses
_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_
_ZSt4cout
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc
_ZNSt8ios_base4InitC1Ev
_ZNSt8ios_base4InitD1Ev
_ZNSolsEPFRSoS_E
__gxx_personality_v0
libm.so.6
libgcc_s.so.1
libc.so.6
_IO_stdin_used
__cxa_atexit
__libc_start_main
CXXABI_1.3
GLIBCXX_3.4
GLIBC_2.0
GLIBC_2.1.3
PTRhp
[^_]
Hello world*[COLOR="Red"]         <-- aha! I knew it![/COLOR]*
GCC: (Ubuntu 4.4.1-4ubuntu8) 4.4.1
GCC: (Ubuntu 4.4.1-4ubuntu9) 4.4.1
_IO_stdin_used
../sysdeps/i386/elf/start.S
/build/buildd/eglibc-2.10.1/csu
GNU AS 2.20
../sysdeps/i386/elf
start.S
3!4=%"
 YZ!"\[
init.c
/build/buildd/eglibc-2.10.1/csu
short unsigned int
GNU C 4.4.1
short int
_IO_stdin_used
long long unsigned int
unsigned char
init.c
long long int
.symtab
.strtab
.shstrtab
.interp
.note.ABI-tag
.note.gnu.build-id
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rel.dyn
.rel.plt
.init
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.ctors
.dtors
.jcr
.dynamic
.got
.got.plt
.data
.bss
.comment
.debug_aranges
.debug_pubnames
.debug_info
.debug_abbrev
.debug_line
.debug_str
init.c
crtstuff.c
__CTOR_LIST__
__DTOR_LIST__
__JCR_LIST__
__do_global_dtors_aux
completed.6990
dtor_idx.6992
frame_dummy
__CTOR_END__
__FRAME_END__
__JCR_END__
__do_global_ctors_aux
sample.cpp
_ZStL8__ioinit
_Z41__static_initialization_and_destruction_0ii
_GLOBAL__I_main
_GLOBAL_OFFSET_TABLE_
__init_array_end
__init_array_start
_DYNAMIC
data_start
__cxa_atexit@@GLIBC_2.1.3
__libc_csu_fini
_start
__gmon_start__
_Jv_RegisterClasses
_fp_hw
_fini
_ZNSt8ios_base4InitC1Ev@@GLIBCXX_3.4
__libc_start_main@@GLIBC_2.0
_ZNSt8ios_base4InitD1Ev@@GLIBCXX_3.4
_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@@GLIBCXX_3.4
_IO_stdin_used
__data_start
_ZSt4cout@@GLIBCXX_3.4
__dso_handle
__DTOR_END__
__libc_csu_init
__bss_start
_end
_ZNSolsEPFRSoS_E@@GLIBCXX_3.4
_ZSt4endlIcSt11char_traitsIcEERSt13basic_ostreamIT_T0_ES6_@@GLIBCXX_3.4
_edata
__gxx_personality_v0@@CXXABI_1.3
__i686.get_pc_thunk.bx
main
_init
[/I]

```

**I think that ^ is *really*, really interesting!** Can anyone with more knowledge suggest where I can read more about the structure of the assemblers' output files and the more advanced details about linking, etc.?

Thanks :)

---

### Post by Simian Man on 2010-01-25
If you are interested in this kind of thing, the book to read is "Linkers and Loaders" by John R. Levine.  It is pretty much *the* book in this area.

BTW that's an ELF file, not an a.out one.  The a.out format is deprecated, though the name is kept.

---

### Post by jzacsh on 2010-01-25
> **Simian Man said:**
> If you are interested in this kind of thing, the book to read is "Linkers and Loaders" by John R. Levine.  It is pretty much *the* book in this area.
Awesome. Thanks, I'll hop on that :)
> **Simian Man said:**
> BTW that's an ELF file, not an a.out one.  The a.out format is deprecated, though the name is kept.
Thanks, yeah the [article I'm reading]("http://www.tldp.org/HOWTO/Software-Building-HOWTO.html") explains that too.

---

