---
title: "need help with patching kernel .rej file"
date: 2014-01-30
forum: Programming Talk
---

### Post by pramitkumarpal on 2014-01-30
I have been trying to patch stable kernel 3.12.5 with Brain **** Scheduler patch (3.12-sched-bfs-444.patch) and config from generic ubuntu 12.04 (config-3.5.0-45-generic) without git.
Lots of Hunks failed and I got a p1.rej file in the linux folder.

I need to understand how to rectify the reject file and produce the patch successfully. 
I am a student of Undergraduate Level Computer Applications and trying my hand at kernel development.

I have a book of Linux Kernel Development - Robert Love and read some parts of the Book The Design of the UNIX Operating system, still unable to figure out how to rectify from the .rej files and online documentation is too vague can't find any useful info.

Please name me a book which can help me with the patching process or give me ur knowledge or give me any good info from any website ... :confused: 

Code from the .rej file is given below 
```

Index: sched.c
--- sched.c    2013-12-03 20:12:21.186148542 +1100
+++ sched.c    2013-12-03 20:12:21.153148955 +1100
@@ -64,11 +64,6 @@
 static struct timer_list spuloadavg_timer;
 
 /*
- * Priority of a normal, non-rt, non-niced'd process (aka nice level 0).
- */
-#define NORMAL_PRIO        120
-
-/*
  * Frequency of the spu scheduler tick.  By default we do one SPU scheduler
  * tick for every 10 CPU scheduler ticks.
  */
Index: kernel.txt
--- kernel.txt    2013-12-03 20:12:21.186148542 +1100
+++ kernel.txt    2013-12-03 20:12:21.155148930 +1100
@@ -33,6 +33,7 @@
 - domainname
 - hostname
 - hotplug
+- iso_cpu
 - kptr_restrict
 - kstack_depth_to_print       [ X86 only ]
 - l2cr                        [ PPC only ]
@@ -60,6 +61,7 @@
 - randomize_va_space
 - real-root-dev               ==> Documentation/initrd.txt
 - reboot-cmd                  [ SPARC only ]
+- rr_interval
 - rtsig-max
 - rtsig-nr
 - sem
@@ -307,6 +309,16 @@
 
 ==============================================================
 
+iso_cpu: (BFS CPU scheduler only).
+
+This sets the percentage cpu that the unprivileged SCHED_ISO tasks can
+run effectively at realtime priority, averaged over a rolling five
+seconds over the -whole- system, meaning all cpus.
+
+Set to 70 (percent) by default.
+
+==============================================================
+
 l2cr: (PPC only)
 
 This flag controls the L2 cache of G3 processor boards. If
@@ -565,6 +577,20 @@
 
 ==============================================================
 
+rr_interval: (BFS CPU scheduler only)
+
+This is the smallest duration that any cpu process scheduling unit
+will run for. Increasing this value can increase throughput of cpu
+bound tasks substantially but at the expense of increased latencies
+overall. Conversely decreasing it will decrease average and maximum
+latencies but at the expense of throughput. This value is in
+milliseconds and the default value chosen depends on the number of
+cpus available at scheduler initialisation with a minimum of 6.
+
+Valid values are from 1-1000.
+
+==============================================================
+
 rtsig-max & rtsig-nr:
 
 The file rtsig-max can be used to tune the maximum number
Index: base.c
--- base.c    2013-12-03 20:12:21.186148542 +1100
+++ base.c    2013-12-03 20:12:21.157148905 +1100
@@ -339,7 +339,7 @@
 static int proc_pid_schedstat(struct task_struct *task, char *buffer)
 {
     return sprintf(buffer, "%llu %llu %lu\n",
-            (unsigned long long)task->se.sum_exec_runtime,
+            (unsigned long long)tsk_seruntime(task),
             (unsigned long long)task->sched_info.run_delay,
             task->sched_info.pcount);
 }
Index: init_task.h
--- init_task.h    2013-12-03 20:12:21.186148542 +1100
+++ init_task.h    2013-12-03 20:12:21.157148905 +1100
@@ -152,12 +152,70 @@
 # define INIT_VTIME(tsk)
 #endif
 
-#define INIT_TASK_COMM "swapper"
-
 /*
  *  INIT_TASK is used to set up the first task table, touch at
  * your own risk!. Base=0, limit=0x1fffff (=2MB)
  */
+#ifdef CONFIG_SCHED_BFS
+#define INIT_TASK_COMM "BFS"
+#define INIT_TASK(tsk)    \
+{                                    \
+    .state        = 0,                        \
+    .stack        = &init_thread_info,                \
+    .usage        = ATOMIC_INIT(2),                \
+    .flags        = PF_KTHREAD,                    \
+    .prio        = NORMAL_PRIO,                    \
+    .static_prio    = MAX_PRIO-20,                    \
+    .normal_prio    = NORMAL_PRIO,                    \
+    .deadline    = 0,                        \
+    .policy        = SCHED_NORMAL,                    \
+    .cpus_allowed    = CPU_MASK_ALL,                    \
+    .mm        = NULL,                        \
+    .active_mm    = &init_mm,                    \
+    .run_list    = LIST_HEAD_INIT(tsk.run_list),            \
+    .time_slice    = HZ,                    \
+    .tasks        = LIST_HEAD_INIT(tsk.tasks),            \
+    INIT_PUSHABLE_TASKS(tsk)                    \
+    .ptraced    = LIST_HEAD_INIT(tsk.ptraced),            \
+    .ptrace_entry    = LIST_HEAD_INIT(tsk.ptrace_entry),        \
+    .real_parent    = &tsk,                        \
+    .parent        = &tsk,                        \
+    .children    = LIST_HEAD_INIT(tsk.children),            \
+    .sibling    = LIST_HEAD_INIT(tsk.sibling),            \
+    .group_leader    = &tsk,                        \
+    RCU_POINTER_INITIALIZER(real_cred, &init_cred),            \
+    RCU_POINTER_INITIALIZER(cred, &init_cred),            \
+    .comm        = INIT_TASK_COMM,                \
+    .thread        = INIT_THREAD,                    \
+    .fs        = &init_fs,                    \
+    .files        = &init_files,                    \
+    .signal        = &init_signals,                \
+    .sighand    = &init_sighand,                \
+    .nsproxy    = &init_nsproxy,                \
+    .pending    = {                        \
+        .list = LIST_HEAD_INIT(tsk.pending.list),        \
+        .signal = {{0}}},                    \
+    .blocked    = {{0}},                    \
+    .alloc_lock    = __SPIN_LOCK_UNLOCKED(tsk.alloc_lock),        \
+    .journal_info    = NULL,                        \
+    .cpu_timers    = INIT_CPU_TIMERS(tsk.cpu_timers),        \
+    .pi_lock    = __RAW_SPIN_LOCK_UNLOCKED(tsk.pi_lock),        \
+    .timer_slack_ns = 50000, /* 50 usec default slack */        \
+    .pids = {                            \
+        [PIDTYPE_PID]  = INIT_PID_LINK(PIDTYPE_PID),        \
+        [PIDTYPE_PGID] = INIT_PID_LINK(PIDTYPE_PGID),        \
+        [PIDTYPE_SID]  = INIT_PID_LINK(PIDTYPE_SID),        \
+    },                                \
+    INIT_IDS                            \
+    INIT_PERF_EVENTS(tsk)                        \
+    INIT_TRACE_IRQFLAGS                        \
+    INIT_LOCKDEP                            \
+    INIT_FTRACE_GRAPH                        \
+    INIT_TRACE_RECURSION                        \
+    INIT_TASK_RCU_PREEMPT(tsk)                    \
+}
+#else /* CONFIG_SCHED_BFS */
+#define INIT_TASK_COMM "swapper"
 #define INIT_TASK(tsk)    \
 {                                    \
     .state        = 0,                        \
@@ -223,7 +281,7 @@
     INIT_CPUSET_SEQ                            \
     INIT_VTIME(tsk)                            \
 }
-
+#endif /* CONFIG_SCHED_BFS */
 
 #define INIT_CPU_TIMERS(cpu_timers)                    \
 {                                    \
Index: ioprio.h
--- ioprio.h    2013-12-03 20:12:21.186148542 +1100
+++ ioprio.h    2013-12-03 20:12:21.158148892 +1100
@@ -52,6 +52,8 @@
  */
 static inline int task_nice_ioprio(struct task_struct *task)
 {
+    if (iso_task(task))
+        return 0;
     return (task_nice(task) + 20) / 5;
 }
 
Index: sched.h
--- sched.h    2013-12-03 20:12:21.186148542 +1100
+++ sched.h    2013-12-03 20:12:21.159148880 +1100
@@ -221,8 +221,6 @@
 extern void init_idle(struct task_struct *idle, int cpu);
 extern void init_idle_bootup_task(struct task_struct *idle);
 
-extern int runqueue_is_locked(int cpu);
-
 #if defined(CONFIG_SMP) && defined(CONFIG_NO_HZ_COMMON)
 extern void nohz_balance_enter_idle(int cpu);
 extern void set_cpu_sd_state_idle(void);
@@ -1023,20 +1021,39 @@
     unsigned int flags;    /* per process flags, defined below */
     unsigned int ptrace;
 
-#ifdef CONFIG_SMP
+#if defined(CONFIG_SMP) || defined(CONFIG_SCHED_BFS)
     struct llist_node wake_entry;
     int on_cpu;
+#endif
+#ifdef CONFIG_SMP
     struct task_struct *last_wakee;
     unsigned long wakee_flips;
     unsigned long wakee_flip_decay_ts;
 #endif
+#ifndef CONFIG_SCHED_BFS
     int on_rq;
+#endif
 
     int prio, static_prio, normal_prio;
     unsigned int rt_priority;
+#ifdef CONFIG_SCHED_BFS
+    int time_slice;
+    u64 deadline;
+    struct list_head run_list;
+    u64 last_ran;
+    u64 sched_time; /* sched_clock time spent running */
+#ifdef CONFIG_SMP
+    bool sticky; /* Soft affined flag */
+#endif
+#ifdef CONFIG_HOTPLUG_CPU
+    bool zerobound; /* Bound to CPU0 for hotplug */
+#endif
+    unsigned long rt_timeout;
+#else /* CONFIG_SCHED_BFS */
     const struct sched_class *sched_class;
     struct sched_entity se;
     struct sched_rt_entity rt;
+#endif
 #ifdef CONFIG_CGROUP_SCHED
     struct task_group *sched_task_group;
 #endif
@@ -1150,6 +1167,9 @@
     int __user *clear_child_tid;        /* CLONE_CHILD_CLEARTID */
 
     cputime_t utime, stime, utimescaled, stimescaled;
+#ifdef CONFIG_SCHED_BFS
+    unsigned long utime_pc, stime_pc;
+#endif
     cputime_t gtime;
 #ifndef CONFIG_VIRT_CPU_ACCOUNTING_NATIVE
     struct cputime prev_cputime;
@@ -1409,6 +1429,64 @@
 #endif
 };
 
+#ifdef CONFIG_SCHED_BFS
+bool grunqueue_is_locked(void);
+void grq_unlock_wait(void);
+void cpu_scaling(int cpu);
+void cpu_nonscaling(int cpu);
+bool above_background_load(void);
+#define tsk_seruntime(t)        ((t)->sched_time)
+#define tsk_rttimeout(t)        ((t)->rt_timeout)
+
+static inline void tsk_cpus_current(struct task_struct *p)
+{
+}
+
+static inline int runqueue_is_locked(int cpu)
+{
+    return grunqueue_is_locked();
+}
+
+void print_scheduler_version(void);
+
+static inline bool iso_task(struct task_struct *p)
+{
+    return (p->policy == SCHED_ISO);
+}
+#else /* CFS */
+extern int runqueue_is_locked(int cpu);
+static inline void cpu_scaling(int cpu)
+{
+}
+
+static inline void cpu_nonscaling(int cpu)
+{
+}
+#define tsk_seruntime(t)    ((t)->se.sum_exec_runtime)
+#define tsk_rttimeout(t)    ((t)->rt.timeout)
+
+static inline void tsk_cpus_current(struct task_struct *p)
+{
+    p->nr_cpus_allowed = current->nr_cpus_allowed;
+}
+
+static inline void print_scheduler_version(void)
+{
+    printk(KERN_INFO"CFS CPU scheduler.\n");
+}
+
+static inline bool iso_task(struct task_struct *p)
+{
+    return false;
+}
+
+/* Anyone feel like implementing this? */
+static inline bool above_background_load(void)
+{
+    return false;
+}
+#endif /* CONFIG_SCHED_BFS */
+
 /* Future-safe accessor for struct task_struct's cpus_allowed. */
 #define tsk_cpus_allowed(tsk) (&(tsk)->cpus_allowed)
 
@@ -1840,7 +1918,7 @@
 task_sched_runtime(struct task_struct *task);
 
 /* sched_exec is called by processes performing an exec */
-#ifdef CONFIG_SMP
+#if defined(CONFIG_SMP) && !defined(CONFIG_SCHED_BFS)
 extern void sched_exec(void);
 #else
 #define sched_exec()   {}
@@ -2554,7 +2632,7 @@
     return 0;
 }
 
-static inline void set_task_cpu(struct task_struct *p, unsigned int cpu)
+static inline void set_task_cpu(struct task_struct *p, int cpu)
 {
 }
 
Index: Kconfig
--- Kconfig    2013-12-03 20:12:21.186148542 +1100
+++ Kconfig    2013-12-03 20:12:21.160148867 +1100
@@ -28,6 +28,20 @@
 
 menu "General setup"
 
+config SCHED_BFS
+    bool "BFS cpu scheduler"
+    ---help---
+      The Brain **** CPU Scheduler for excellent interactivity and
+      responsiveness on the desktop and solid scalability on normal
+          hardware and commodity servers. Not recommended for 4096 CPUs.
+
+      Currently incompatible with the Group CPU scheduler, and RCU TORTURE
+          TEST so these options are disabled.
+
+          Say Y here.
+    default y
+
+
 config BROKEN
     bool
 
@@ -331,7 +345,7 @@
 # Kind of a stub config for the pure tick based cputime accounting
 config TICK_CPU_ACCOUNTING
     bool "Simple tick based cputime accounting"
-    depends on !S390 && !NO_HZ_FULL
+    depends on !S390 && !NO_HZ_FULL && !SCHED_BFS
     help
       This is the basic tick based cputime accounting that maintains
       statistics about user, system and idle time spent on per jiffies
@@ -354,7 +368,7 @@
 
 config VIRT_CPU_ACCOUNTING_GEN
     bool "Full dynticks CPU time accounting"
-    depends on HAVE_CONTEXT_TRACKING && 64BIT
+    depends on HAVE_CONTEXT_TRACKING && 64BIT && !SCHED_BFS
     select VIRT_CPU_ACCOUNTING
     select CONTEXT_TRACKING
     help
@@ -510,7 +524,7 @@
 
 config RCU_USER_QS
     bool "Consider userspace as in RCU extended quiescent state"
-    depends on HAVE_CONTEXT_TRACKING && SMP
+    depends on HAVE_CONTEXT_TRACKING && SMP && !SCHED_BFS
     select CONTEXT_TRACKING
     help
       This option sets hooks on kernel / userspace boundaries and
@@ -695,7 +709,7 @@
 
 config RCU_NOCB_CPU
     bool "Offload RCU callback processing from boot-selected CPUs"
-    depends on TREE_RCU || TREE_PREEMPT_RCU
+    depends on (TREE_RCU || TREE_PREEMPT_RCU) && !SCHED_BFS
     default n
     help
       Use this option to reduce OS jitter for aggressive HPC or
@@ -852,6 +866,7 @@
     depends on ARCH_SUPPORTS_NUMA_BALANCING
     depends on !ARCH_WANT_NUMA_VARIABLE_LOCALITY
     depends on SMP && NUMA && MIGRATION
+    depends on !SCHED_BFS
     help
       This option adds support for automatic NUMA aware memory/task placement.
       The mechanism is quite primitive and is based on migrating memory when
@@ -914,6 +929,7 @@
 
 config CGROUP_CPUACCT
     bool "Simple CPU accounting cgroup subsystem"
+    depends on !SCHED_BFS
     help
       Provides a simple Resource Controller for monitoring the
       total CPU consumed by the tasks in a cgroup.
@@ -1016,6 +1032,7 @@
 
 menuconfig CGROUP_SCHED
     bool "Group CPU scheduler"
+    depends on !SCHED_BFS
     default n
     help
       This feature lets CPU scheduler recognize task groups and control CPU
@@ -1167,6 +1184,7 @@
 
 config SCHED_AUTOGROUP
     bool "Automatic process group scheduling"
+    depends on !SCHED_BFS
     select EVENTFD
     select CGROUPS
     select CGROUP_SCHED
@@ -1567,38 +1585,8 @@
 
       On non-ancient distros (post-2000 ones) N is usually a safe choice.
 
-choice
-    prompt "Choose SLAB allocator"
-    default SLUB
-    help
-       This option allows to select a slab allocator.
-
-config SLAB
-    bool "SLAB"
-    help
-      The regular slab allocator that is established and known to work
-      well in all environments. It organizes cache hot objects in
-      per cpu and per node queues.
-
 config SLUB
-    bool "SLUB (Unqueued Allocator)"
-    help
-       SLUB is a slab allocator that minimizes cache line usage
-       instead of managing queues of cached objects (SLAB approach).
-       Per cpu caching is realized using slabs of objects instead
-       of queues of objects. SLUB can use memory efficiently
-       and has enhanced diagnostics. SLUB is the default choice for
-       a slab allocator.
-
-config SLOB
-    depends on EXPERT
-    bool "SLOB (Simple Allocator)"
-    help
-       SLOB replaces the stock allocator with a drastically simpler
-       allocator. SLOB is generally more space efficient but
-       does not perform as well on large systems.
-
-endchoice
+    def_bool y
 
 config SLUB_CPU_PARTIAL
     default y
Index: main.c
--- main.c    2013-12-03 20:12:21.186148542 +1100
+++ main.c    2013-12-03 20:12:21.161148855 +1100
@@ -704,7 +704,6 @@
     return ret;
 }
 
-
 extern initcall_t __initcall_start[];
 extern initcall_t __initcall0_start[];
 extern initcall_t __initcall1_start[];
@@ -825,6 +824,8 @@
 
     flush_delayed_fput();
 
+    print_scheduler_version();
+
     if (ramdisk_execute_command) {
         if (!run_init_process(ramdisk_execute_command))
             return 0;
Index: delayacct.c
--- delayacct.c    2013-12-03 20:12:21.186148542 +1100
+++ delayacct.c    2013-12-03 20:12:21.162148842 +1100
@@ -133,7 +133,7 @@
      */
     t1 = tsk->sched_info.pcount;
     t2 = tsk->sched_info.run_delay;
-    t3 = tsk->se.sum_exec_runtime;
+    t3 = tsk_seruntime(tsk);
 
     d->cpu_count += t1;
 
Index: exit.c
--- exit.c    2013-12-03 20:12:21.186148542 +1100
+++ exit.c    2013-12-03 20:12:21.163148830 +1100
@@ -135,7 +135,7 @@
         sig->inblock += task_io_get_inblock(tsk);
         sig->oublock += task_io_get_oublock(tsk);
         task_io_accounting_add(&sig->ioac, &tsk->ioac);
-        sig->sum_sched_runtime += tsk->se.sum_exec_runtime;
+        sig->sum_sched_runtime += tsk_seruntime(tsk);
     }
 
     sig->nr_threads--;
Index: posix-cpu-timers.c
--- posix-cpu-timers.c    2013-12-03 20:12:21.186148542 +1100
+++ posix-cpu-timers.c    2013-12-03 20:12:21.163148830 +1100
@@ -435,11 +435,11 @@
 {
     cputime_t utime, stime;
 
-    add_device_randomness((const void*) &tsk->se.sum_exec_runtime,
+    add_device_randomness((const void*) &tsk_seruntime(tsk),
                         sizeof(unsigned long long));
     task_cputime(tsk, &utime, &stime);
     cleanup_timers(tsk->cpu_timers,
-               utime, stime, tsk->se.sum_exec_runtime);
+               utime, stime, tsk_seruntime(tsk));
 
 }
 void posix_cpu_timers_exit_group(struct task_struct *tsk)
@@ -450,7 +450,7 @@
     task_cputime(tsk, &utime, &stime);
     cleanup_timers(tsk->signal->cpu_timers,
                utime + sig->utime, stime + sig->stime,
-               tsk->se.sum_exec_runtime + sig->sum_sched_runtime);
+               tsk_seruntime(tsk) + sig->sum_sched_runtime);
 }
 
 static void clear_dead_task(struct k_itimer *itimer, unsigned long long now)
@@ -905,7 +905,7 @@
     tsk_expires->virt_exp = expires_to_cputime(expires);
 
     tsk_expires->sched_exp = check_timers_list(++timers, firing,
-                           tsk->se.sum_exec_runtime);
+                           tsk_seruntime(tsk));
 
     /*
      * Check for the special case thread timers.
@@ -916,7 +916,7 @@
             ACCESS_ONCE(sig->rlim[RLIMIT_RTTIME].rlim_max);
 
         if (hard != RLIM_INFINITY &&
-            tsk->rt.timeout > DIV_ROUND_UP(hard, USEC_PER_SEC/HZ)) {
+            tsk_rttimeout(tsk) > DIV_ROUND_UP(hard, USEC_PER_SEC/HZ)) {
             /*
              * At the hard limit, we just die.
              * No need to calculate anything else now.
@@ -924,7 +924,7 @@
             __group_send_sig_info(SIGKILL, SEND_SIG_PRIV, tsk);
             return;
         }
-        if (tsk->rt.timeout > DIV_ROUND_UP(soft, USEC_PER_SEC/HZ)) {
+        if (tsk_rttimeout(tsk) > DIV_ROUND_UP(soft, USEC_PER_SEC/HZ)) {
             /*
              * At the soft limit, send a SIGXCPU every second.
              */
@@ -1167,7 +1167,7 @@
         struct task_cputime task_sample = {
             .utime = utime,
             .stime = stime,
-            .sum_exec_runtime = tsk->se.sum_exec_runtime
+            .sum_exec_runtime = tsk_seruntime(tsk)
         };
 
         if (task_cputime_expired(&task_sample, &tsk->cputime_expires))
Index: sysctl.c
--- sysctl.c    2013-12-03 20:12:21.186148542 +1100
+++ sysctl.c    2013-12-03 20:12:21.164148817 +1100
@@ -127,7 +127,12 @@
 static int __maybe_unused two = 2;
 static int __maybe_unused three = 3;
 static unsigned long one_ul = 1;
-static int one_hundred = 100;
+static int __maybe_unused one_hundred = 100;
+#ifdef CONFIG_SCHED_BFS
+extern int rr_interval;
+extern int sched_iso_cpu;
+static int __read_mostly one_thousand = 1000;
+#endif
 #ifdef CONFIG_PRINTK
 static int ten_thousand = 10000;
 #endif
@@ -255,7 +260,7 @@
     { }
 };
 
-#ifdef CONFIG_SCHED_DEBUG
+#if defined(CONFIG_SCHED_DEBUG) && !defined(CONFIG_SCHED_BFS)
 static int min_sched_granularity_ns = 100000;        /* 100 usecs */
 static int max_sched_granularity_ns = NSEC_PER_SEC;    /* 1 second */
 static int min_wakeup_granularity_ns;            /* 0 usecs */
@@ -272,6 +277,7 @@
 #endif
 
 static struct ctl_table kern_table[] = {
+#ifndef CONFIG_SCHED_BFS
     {
         .procname    = "sched_child_runs_first",
         .data        = &sysctl_sched_child_runs_first,
@@ -435,6 +441,7 @@
         .extra1        = &one,
     },
 #endif
+#endif /* !CONFIG_SCHED_BFS */
 #ifdef CONFIG_PROVE_LOCKING
     {
         .procname    = "prove_locking",
@@ -913,6 +920,26 @@
         .proc_handler    = proc_dointvec,
     },
 #endif
+#ifdef CONFIG_SCHED_BFS
+    {
+        .procname    = "rr_interval",
+        .data        = &rr_interval,
+        .maxlen        = sizeof (int),
+        .mode        = 0644,
+        .proc_handler    = &proc_dointvec_minmax,
+        .extra1        = &one,
+        .extra2        = &one_thousand,
+    },
+    {
+        .procname    = "iso_cpu",
+        .data        = &sched_iso_cpu,
+        .maxlen        = sizeof (int),
+        .mode        = 0644,
+        .proc_handler    = &proc_dointvec_minmax,
+        .extra1        = &zero,
+        .extra2        = &one_hundred,
+    },
+#endif
 #if defined(CONFIG_S390) && defined(CONFIG_SMP)
     {
         .procname    = "spin_retry",
Index: Kconfig.debug
--- Kconfig.debug    2013-12-03 20:12:21.186148542 +1100
+++ Kconfig.debug    2013-12-03 20:12:21.165148805 +1100
@@ -1125,7 +1125,7 @@
 
 config RCU_TORTURE_TEST
     tristate "torture tests for RCU"
-    depends on DEBUG_KERNEL
+    depends on DEBUG_KERNEL && !SCHED_BFS
     default n
     help
       This option provides a kernel module that runs torture tests
Index: jiffies.h
--- jiffies.h    2013-12-03 20:12:21.186148542 +1100
+++ jiffies.h    2013-12-03 20:12:21.166148792 +1100
@@ -163,7 +163,7 @@
  * Have the 32 bit jiffies value wrap 5 minutes after boot
  * so jiffies wrap bugs show up earlier.
  */
-#define INITIAL_JIFFIES ((unsigned long)(unsigned int) (-300*HZ))
+#define INITIAL_JIFFIES ((unsigned long)(unsigned int) (-10*HZ))
 
 /*
  * Change timeval to jiffies, trying to avoid the
Index: cpufreq.c
--- cpufreq.c    2013-12-03 20:12:21.186148542 +1100
+++ cpufreq.c    2013-12-03 20:12:21.167148780 +1100
@@ -25,6 +25,7 @@
 #include <linux/kernel_stat.h>
 #include <linux/module.h>
 #include <linux/mutex.h>
+#include <linux/sched.h>
 #include <linux/slab.h>
 #include <linux/syscore_ops.h>
 #include <linux/tick.h>
@@ -1686,6 +1687,12 @@
 
     if (cpufreq_driver->target)
         retval = cpufreq_driver->target(policy, target_freq, relation);
+    if (likely(retval != -EINVAL)) {
+        if (target_freq == policy->max)
+            cpu_nonscaling(policy->cpu);
+        else
+            cpu_scaling(policy->cpu);
+    }
 
     return retval;
 }
Index: cpufreq_ondemand.c
--- cpufreq_ondemand.c    2013-12-03 20:12:21.186148542 +1100
+++ cpufreq_ondemand.c    2013-12-03 20:12:21.168148767 +1100
@@ -19,7 +19,7 @@
 #include "cpufreq_governor.h"
 
 /* On-demand governor macros */
-#define DEF_FREQUENCY_UP_THRESHOLD        (80)
+#define DEF_FREQUENCY_UP_THRESHOLD        (63)
 #define DEF_SAMPLING_DOWN_FACTOR        (1)
 #define MAX_SAMPLING_DOWN_FACTOR        (100000)
 #define MICRO_FREQUENCY_UP_THRESHOLD        (95)
@@ -148,7 +148,7 @@
 }
 
 /*
- * Every sampling_rate, we check, if current idle time is less than 20%
+ * Every sampling_rate, we check, if current idle time is less than 37%
  * (default), then we try to increase frequency. Else, we adjust the frequency
  * proportional to load.
  */
Index: sched.h
--- sched.h    2013-12-03 20:12:21.186148542 +1100
+++ sched.h    2013-12-03 20:12:21.173148705 +1100
@@ -37,8 +37,15 @@
 #define SCHED_FIFO        1
 #define SCHED_RR        2
 #define SCHED_BATCH        3
-/* SCHED_ISO: reserved but not implemented yet */
+/* SCHED_ISO: Implemented on BFS only */
 #define SCHED_IDLE        5
+#ifdef CONFIG_SCHED_BFS
+#define SCHED_ISO        4
+#define SCHED_IDLEPRIO        SCHED_IDLE
+#define SCHED_MAX        (SCHED_IDLEPRIO)
+#define SCHED_RANGE(policy)    ((policy) <= SCHED_MAX)
+#endif
+
 /* Can be ORed in to make sure the process is reverted back to SCHED_NORMAL on fork */
 #define SCHED_RESET_ON_FORK     0x40000000
 
Index: rt.h
--- rt.h    2013-12-03 20:12:21.186148542 +1100
+++ rt.h    2013-12-03 20:12:21.173148705 +1100
@@ -14,11 +14,24 @@
  * MAX_RT_PRIO must not be smaller than MAX_USER_RT_PRIO.
  */
 
+#ifdef CONFIG_SCHED_BFS
+#define MAX_USER_RT_PRIO    100
+#define MAX_RT_PRIO        (MAX_USER_RT_PRIO + 1)
+#define DEFAULT_PRIO        (MAX_RT_PRIO + 20)
+
+#define PRIO_RANGE        (40)
+#define MAX_PRIO        (MAX_RT_PRIO + PRIO_RANGE)
+#define ISO_PRIO        (MAX_RT_PRIO)
+#define NORMAL_PRIO        (MAX_RT_PRIO + 1)
+#define IDLE_PRIO        (MAX_RT_PRIO + 2)
+#define PRIO_LIMIT        ((IDLE_PRIO) + 1)
+#else /* CONFIG_SCHED_BFS */
 #define MAX_USER_RT_PRIO    100
 #define MAX_RT_PRIO        MAX_USER_RT_PRIO
 
 #define MAX_PRIO        (MAX_RT_PRIO + 40)
 #define DEFAULT_PRIO        (MAX_RT_PRIO + 20)
+#endif /* CONFIG_SCHED_BFS */
 
 static inline int rt_prio(int prio)
 {
Index: stop_machine.c
--- stop_machine.c    2013-12-03 20:12:21.186148542 +1100
+++ stop_machine.c    2013-12-03 20:12:21.174148692 +1100
@@ -40,7 +40,8 @@
 };
 
 static DEFINE_PER_CPU(struct cpu_stopper, cpu_stopper);
-static DEFINE_PER_CPU(struct task_struct *, cpu_stopper_task);
+DEFINE_PER_CPU(struct task_struct *, cpu_stopper_task);
+
 static bool stop_machine_initialized = false;
 
 static void cpu_stop_init_done(struct cpu_stop_done *done, unsigned int nr_todo)
Index: cpufreq_conservative.c
--- cpufreq_conservative.c    2013-12-03 20:12:21.186148542 +1100
+++ cpufreq_conservative.c    2013-12-03 20:12:21.174148692 +1100
@@ -15,8 +15,8 @@
 #include "cpufreq_governor.h"
 
 /* Conservative governor macros */
-#define DEF_FREQUENCY_UP_THRESHOLD        (80)
-#define DEF_FREQUENCY_DOWN_THRESHOLD        (20)
+#define DEF_FREQUENCY_UP_THRESHOLD        (63)
+#define DEF_FREQUENCY_DOWN_THRESHOLD        (26)
 #define DEF_FREQUENCY_STEP            (5)
 #define DEF_SAMPLING_DOWN_FACTOR        (1)
 #define MAX_SAMPLING_DOWN_FACTOR        (10)
Index: Kconfig
--- Kconfig    2013-12-03 20:12:21.186148542 +1100
+++ Kconfig    2013-12-03 20:12:21.175148680 +1100
@@ -94,7 +94,7 @@
 config NO_HZ_FULL
     bool "Full dynticks system (tickless)"
     # NO_HZ_COMMON dependency
-    depends on !ARCH_USES_GETTIMEOFFSET && GENERIC_CLOCKEVENTS
+    depends on !ARCH_USES_GETTIMEOFFSET && GENERIC_CLOCKEVENTS && !SCHED_BFS
     # We need at least one periodic CPU for timekeeping
     depends on SMP
     # RCU_USER_QS dependency
Index: Makefile
--- Makefile    2013-12-03 20:12:21.186148542 +1100
+++ Makefile    2013-12-03 20:12:21.176148667 +1100
@@ -11,9 +11,13 @@
 CFLAGS_core.o := $(PROFILING) -fno-omit-frame-pointer
 endif
 
+ifdef CONFIG_SCHED_BFS
+obj-y += bfs.o clock.o
+else
 obj-y += core.o proc.o clock.o cputime.o idle_task.o fair.o rt.o stop_task.o
-obj-$(CONFIG_SMP) += cpupri.o
 obj-$(CONFIG_SCHED_AUTOGROUP) += auto_group.o
-obj-$(CONFIG_SCHEDSTATS) += stats.o
 obj-$(CONFIG_SCHED_DEBUG) += debug.o
 obj-$(CONFIG_CGROUP_CPUACCT) += cpuacct.o
+endif
+obj-$(CONFIG_SMP) += cpupri.o
+obj-$(CONFIG_SCHEDSTATS) += stats.o
Index: bfs_sched.h
--- bfs_sched.h    2013-12-03 20:12:21.176148667 +1100
+++ /dev/null
@@ -1,116 +0,0 @@
-#include <linux/sched.h>
-
-#ifndef BFS_SCHED_H
-#define BFS_SCHED_H
-
-/*
- * This is the main, per-CPU runqueue data structure.
- * This data should only be modified by the local cpu.
- */
-struct rq {
-    struct task_struct *curr, *idle, *stop;
-    struct mm_struct *prev_mm;
-
-    /* Stored data about rq->curr to work outside grq lock */
-    u64 rq_deadline;
-    unsigned int rq_policy;
-    int rq_time_slice;
-    u64 rq_last_ran;
-    int rq_prio;
-    bool rq_running; /* There is a task running */
-
-    /* Accurate timekeeping data */
-    u64 timekeep_clock;
-    unsigned long user_pc, nice_pc, irq_pc, softirq_pc, system_pc,
-        iowait_pc, idle_pc;
-    atomic_t nr_iowait;
-
-#ifdef CONFIG_SMP
-    int cpu;        /* cpu of this runqueue */
-    bool online;
-    bool scaling; /* This CPU is managed by a scaling CPU freq governor */
-    struct task_struct *sticky_task;
-
-    struct root_domain *rd;
-    struct sched_domain *sd;
-    int *cpu_locality; /* CPU relative cache distance */
-#ifdef CONFIG_SCHED_SMT
-    bool (*siblings_idle)(int cpu);
-    /* See if all smt siblings are idle */
-    cpumask_t smt_siblings;
-#endif /* CONFIG_SCHED_SMT */
-#ifdef CONFIG_SCHED_MC
-    bool (*cache_idle)(int cpu);
-    /* See if all cache siblings are idle */
-    cpumask_t cache_siblings;
-#endif /* CONFIG_SCHED_MC */
-    u64 last_niffy; /* Last time this RQ updated grq.niffies */
-#endif /* CONFIG_SMP */
-#ifdef CONFIG_IRQ_TIME_ACCOUNTING
-    u64 prev_irq_time;
-#endif /* CONFIG_IRQ_TIME_ACCOUNTING */
-#ifdef CONFIG_PARAVIRT
-    u64 prev_steal_time;
-#endif /* CONFIG_PARAVIRT */
-#ifdef CONFIG_PARAVIRT_TIME_ACCOUNTING
-    u64 prev_steal_time_rq;
-#endif /* CONFIG_PARAVIRT_TIME_ACCOUNTING */
-
-    u64 clock, old_clock, last_tick;
-    u64 clock_task;
-    bool dither;
-
-#ifdef CONFIG_SCHEDSTATS
-
-    /* latency stats */
-    struct sched_info rq_sched_info;
-    unsigned long long rq_cpu_time;
-    /* could above be rq->cfs_rq.exec_clock + rq->rt_rq.rt_runtime ? */
-
-    /* sys_sched_yield() stats */
-    unsigned int yld_count;
-
-    /* schedule() stats */
-    unsigned int sched_switch;
-    unsigned int sched_count;
-    unsigned int sched_goidle;
-
-    /* try_to_wake_up() stats */
-    unsigned int ttwu_count;
-    unsigned int ttwu_local;
-#endif /* CONFIG_SCHEDSTATS */
-
-#ifdef CONFIG_SMP
-    struct llist_head wake_list;
-#endif
-};
-
-#ifdef CONFIG_SMP
-struct rq *cpu_rq(int cpu);
-#endif
-
-static inline u64 rq_clock(struct rq *rq)
-{
-    return rq->clock;
-}
-
-static inline u64 rq_clock_task(struct rq *rq)
-{
-    return rq->clock_task;
-}
-
-#define rcu_dereference_check_sched_domain(p) \
-    rcu_dereference_check((p), \
-                  lockdep_is_held(&sched_domains_mutex))
-
-/*
- * The domain tree (rq->sd) is protected by RCU's quiescent state transition.
- * See detach_destroy_domains: synchronize_sched for details.
- *
- * The domain tree of any CPU may only be accessed from within
- * preempt-disabled sections.
- */
-#define for_each_domain(cpu, __sd) \
-    for (__sd = rcu_dereference_check_sched_domain(cpu_rq(cpu)->sd); __sd; __sd = __sd->parent)
-
-#endif
Index: stats.c
--- stats.c    2013-12-03 20:12:21.186148542 +1100
+++ stats.c    2013-12-03 20:12:21.176148667 +1100
@@ -4,7 +4,11 @@
 #include <linux/seq_file.h>
 #include <linux/proc_fs.h>
 
+#ifndef CONFIG_SCHED_BFS
 #include "sched.h"
+#else
+#include "bfs_sched.h"
+#endif
 
 /*
  * bump this up when changing the output format or the meaning of an existing

```

---

