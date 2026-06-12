---
title: "Problem - Moonlight 3.0 Preview on Firefox on Ubuntu"
date: 2010-08-12
forum: Programming Talk
---

### Post by Newbie2910 on 2010-08-12
I am writing a Moonlight/Silverlight app.  If I install the Moonlight 2.0 plugin, it works fine.  However, I need the add'l capabilities of 3.0.

If I load the 3.0 Preview plugin, any app I run (even the starter "Hello, World" one the MonoDevelop IDE generates) fails in Firefox:

Thread 1 (Thread 0xb556f770 (LWP 5073)): 
#0  0xb7745430 in __kernel_vsyscall () 
#1  0xb7727f5b in read () from /lib/tls/i686/cmov/libpthread.so.0 
#2  0xadacc365 in print_gdb_trace () at debug.cpp:692 
#3  0xadacd7c1 in moonlight_handle_native_sigsegv (signal=11) at debug.cpp:750 
#4  <signal handler called> 
#5  0xadf35a02 in GC_local_malloc (bytes=40) at pthread_support.c:354 
#6  0xade3c7a4 in mono_g_hash_table_new ( 
    hash_func=0xadf32537 <monoeg_g_direct_hash>,  
    key_equal_func=0xadf32526 <monoeg_g_direct_equal>) at mono-hash.c:164 
#7  0xade3c864 in mono_g_hash_table_new_type (hash_func=0, key_equal_func=0,  
    type=MONO_HASH_KEY_GC) at mono-hash.c:135 
#8  0xaddf1088 in mono_debugger_agent_init () at debugger-agent.c:781 
#9  0xadd54233 in mini_init (filename=0xae0118ef "Moonlight Root Domain",  
    runtime_version=0xae0118e5 "moonlight") at mini.c:5750 
#10 0xadb20804 in Moonlight::Deployment::Initialize ( 
    platform_dir=0xaf0b0380  "/home/me/.mozilla/firefox/schgq5vj.monodevelop-moonlight-debug/extensions/moonlight@novell.com/plugins/moonlight",   
    create_root_domain=true) at deployment.cpp:172 
#11 0xadc17979 in runtime_init ( 
    platform_dir=0xaf0b0380  "/home/me/.mozilla/firefox/schgq5vj.monodevelop-moonlight-debug/extensions/moonlight@novell.com/plugins/moonlight",   
    flags=757872896) at runtime.cpp:2693 
#12 0xadc17a49 in runtime_init_browser ( 
    plugin_dir=0xaf0b0380  "/home/me/.mozilla/firefox/schgq5vj.monodevelop-moonlight-debug/extensions/moonlight@novell.com/plugins/moonlight") 
    at runtime.cpp:2504 
#13 0xada65a80 in MOON_NPP_Initialize () at plugin-glue.cpp:241 
#14 0xada63fd0 in MOON_NP_Initialize (mozilla_funcs=0xb7716c48,  
    plugin_funcs=0xbfc2d520) at plugin-entry.cpp:492 
#15 0xb2900dcf in NP_Initialize (mozilla_funcs=0xb7716c48,  
    plugin_funcs=0xbfc2d520) at plugin-proxy.cpp:169 

I need to find a solution to this.. any suggestions?

Using Ubuntu 10.04 and FireFox 3.6.8

Thanks.

---

