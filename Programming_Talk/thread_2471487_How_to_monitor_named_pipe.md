---
title: "How to monitor named pipe"
date: 2022-01-31
forum: Programming Talk
---

### Post by tc2020 on 2022-01-31
Hello,

I am looking for help on how to monitor a named pipe operational integrity and to take corrective action.

In our application, we have a program running as a systemd service that creates unidirectional named pipes and writes the same data to all pipes. Out of these pipes, one is read by a process that simply writes to a raw data file and the second pipe is read by snmp agent running on snmpd to fill snmp table. From time to time, we see the raw data file stops collecting data. When this happens, we do systemctl restart the program, systemctl status shows it as running active but the raw data file still stays the same as before. However, the moment we systemctl restart snmpd, the raw data file resumes collecting data. It looks like the pipe for snmp agent is the one holding up proper restart of the program.

What seems to be the root cause?. How do we monitor these pipes so that we can correct them somehow?. The brute force approach is to regularly restart snmpd. 

The snmp agent sample code is as shown below:

```
static void* pipe_data_thread_analog(void* arg)
{
    DEBUGMSGTL(("an_tables:pipe_data_thread_analog", "tid = %d\n", gettid()));

    FILE* fp = fopen(pname_analog, "r");
    if ( !fp )
    {
        char errmsg[128];
        char* ptr = strerror_r(errno, errmsg, sizeof(errmsg));
        DEBUGMSGTL(("an_tables:pipe_data_thread_analog", "Could not open pipe, errno = %d(%s)\n", errno, errmsg));
        return 0;
    }

    while(1)
    {
        // Read data
        char buf[2048];
        char* result = fgets(buf, sizeof(buf), fp);
        if(result != 0)
        {
            DEBUGMSGTL(("an_tables:pipe_data_thread_analog", "AI - buf = (%s)\n", buf));

            // Parse analog data
            pthread_mutex_lock(&analog_data_mutex);
            parser_parse_analog_data(buf, &analog_data);
            pthread_mutex_unlock(&analog_data_mutex);
        }
        else
        {
            DEBUGMSGTL(("an_tables:pipe_data_thread_analog", "EOF\n"));
        }
    };

    fclose(fp);

    return(0);
}
```

Any help would be greatly appreciated. Thanks.

---

### Post by MAFoElffen on 2022-02-06
Have you been using the CLI tools snmpget and snmpwalk to verify that there is still some type of communication going on or not, when that occurs?

---

### Post by tc2020 on 2022-02-06
We use Windows software tool to view the table and it was empty in this situation. We will monitor until it gets into this condition again and use CLI to check. The system can go on for days without any problem and for some reason it gets into this state, so very unpredictable.

Besides this, is there a general and reliable technique to monitor named pipes to catch condition as described?.

---

### Post by tc2020 on 2022-02-14
We managed to get into that state and snmpwalk returned correct values.

---

