---
title: "sched_setscheduler() what priv needed on Ubuntu/Debian"
date: 2013-02-09
forum: Programming Talk
---

### Post by yyyc186 on 2013-02-09
On-line documentation really passes gas with this one. Each and every link I find explains EPERM as "user does not have required priv"

The user account has both CAP_SYS_NICE and CAP_SYS_RESOURCE. The following snippet is part of the application.

```

    pid_t ourPid = getpid();
    cap_t ct = cap_init();
    ct = cap_get_pid( ourPid);
    FILE_LOG(logINFO) << "outPid " << ourPid;
    ssize_t y=0;
    FILE_LOG(logINFO) << "process has following capabilities: " << cap_to_text(ct, &y);
    if (CAP_IS_SUPPORTED(CAP_SYS_NICE))
    FILE_LOG(logINFO) << "CAP_SYS_NICE is supported";
    else
    FILE_LOG(logINFO) << "**** CAP_SYS_NICE is NOT supported";
     
    if (CAP_IS_SUPPORTED(CAP_SYS_RESOURCE))
    FILE_LOG(logINFO) << "CAP_SYS_RESOURCE is supported";
    else
    FILE_LOG(logINFO) << "**** CAP_SYS_RESOURCE is NOT supported";
     
    if (cap_free(ct) == -1)
    {
    FILE_LOG(logCRITICAL) << "failed to free cap_t structure";
    }

```

It indicates all is well.

2013-02-08 16:15:51.143034 U: INFO : outPid 9963
2013-02-08 16:15:51.143186 U: INFO : process has following capabilities: = cap_sys_resource+i
2013-02-08 16:15:51.143204 U: INFO : CAP_SYS_NICE is supported
2013-02-08 16:15:51.143215 U: INFO : CAP_SYS_RESOURCE is supported


Account has enough priv for program to execute this:

```

    int p_min, p_max;
    p_max = sched_get_priority_max(SCHED_FIFO);
    p_min = sched_get_priority_min(SCHED_FIFO);
    FILE_LOG(logINFO) << "SCHED_FIFO min " << p_min << " and max " << p_max << " priorities";

```

Process produces

2013-02-08 16:16:01.654126 U: INFO : SCHED_FIFO min 1 and max 99 priorities


Yet the following snippet fails.

```

    if (sched_setscheduler(0, SCHED_FIFO, &sp) == -1)
    {
    cout << "errno from setting scheduler " << errno << " ENOSYS " << ENOSYS << " EPERM " << EPERM << " ESRCH " << ESRCH << endl;
     
    SysUtils::handleLastError("sched_setscheduler()");
    ret = false;
    }

```

errno from setting scheduler 1 ENOSYS 38 EPERM 1 ESRCH 3

What group do I need to put this user in (DON'T SAY ROOT). Where is the link which tells all developers which priv is needed on Ubuntu or Debian?

We are deliberately trying to make this application run as an application under a user account, not ROOT. I have been handing out groups with an eye dropper and now only have this problem to solve. There has to be a group (OTHER THAN ROOT) I can put this user in or a priv I can somehow assign to the account to let it set the scheduler.

Thanks in advance.

---

