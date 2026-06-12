---
title: "Python: execute ping as subprocess with timeout"
date: 2018-07-12
forum: Programming Talk
---

### Post by erotavlas on 2018-07-12
Hi,
I have to measure RTT between several hosts in Internet. In python there are several libraries, however they require root access. For this reason I wrote a simple function that call system ping and parse the output.
```

for host in tqdm(hosts):
    ping=subprocess.Popen(["ping", "-c", "1", "-w", "0.2", host],stdout=subprocess.PIPE, stderr = subprocess.PIPE)
    [out, err]=ping.communicate()
    if ping.returncode == 0:
        avgRTT=re.search("rtt min/avg/max/mdev = (\d+.\d+)/(\d+.\d+)/(\d+.\d+)/(\d+.\d+)", str(out)).group(1)

```
I want to ping an host and timeout if it last over 200 ms (200 ms is the minimum value without having root access).
From man ping, I read that the options -w deadline and -W timeout should do the job, but they does not work as aspected if an host is unreachable.
I already read [here]("https://serverfault.com/questions/200468/how-can-i-set-a-short-timeout-with-the-ping-command/733940#733940") and the only solution is to use fping that is not portable.
Thank you

---

### Post by erotavlas on 2018-07-12
Hi,
I solved by myself with the following code:
```

for host in tqdm(hosts):
    ping=subprocess.Popen(["ping", "-c", "1", proxy[0]],stdout=subprocess.PIPE,stderr=subprocess.PIPE)
        try:             
            [out, err]=ping.communicate(timeout=0.1)
            if ping.returncode == 0:
                avgRTT=re.search("rtt min/avg/max/mdev = (\d+.\d+)/(\d+.\d+)/(\d+.\d+)/(\d+.\d+)", str(out)).group(1)
            except subprocess.TimeoutExpired:
                ping.kill()

```
The only problem is that I have to use python3.3+ since even by installing [subprocess32]("https://pypi.org/project/subprocess32/") does not work for me.

---

### Post by riyawilliams on 2018-07-12
Hai, 
I tried this one, it worked out for me. 
[COLOR=#FF7700]**import**[/COLOR] [COLOR=#DC143C]subprocess[/COLOR]
 
[COLOR=#FF7700]**from**[/COLOR] [COLOR=#DC143C]threading[/COLOR] [COLOR=#FF7700]**import**[/COLOR] Timer
 
kill = [COLOR=#FF7700]**lambda**[/COLOR] process: process.[COLOR=black]kill[/COLOR][COLOR=black]([/COLOR][COLOR=black])[/COLOR]
[COLOR=#DC143C]cmd[/COLOR] = [COLOR=black][[/COLOR][COLOR=#483D8B]'ping'[/COLOR], [COLOR=#483D8B]'www.google.com'[/COLOR][COLOR=black]][/COLOR]
ping = [COLOR=#DC143C]subprocess[/COLOR].[COLOR=black]Popen[/COLOR][COLOR=black]([/COLOR]
    [COLOR=#DC143C]cmd[/COLOR], stdout=[COLOR=#DC143C]subprocess[/COLOR].[COLOR=black]PIPE[/COLOR], stderr=[COLOR=#DC143C]subprocess[/COLOR].[COLOR=black]PIPE[/COLOR][COLOR=black])[/COLOR]
 
my_timer = Timer[COLOR=black]([/COLOR][COLOR=#FF4500]5[/COLOR], kill, [COLOR=black][[/COLOR]ping[COLOR=black]][/COLOR][COLOR=black])[/COLOR]
 
[COLOR=#FF7700]**try**[/COLOR]:
    my_timer.[COLOR=black]start[/COLOR][COLOR=black]([/COLOR][COLOR=black])[/COLOR]
    stdout, stderr = ping.[COLOR=black]communicate[/COLOR][COLOR=black]([/COLOR][COLOR=black])[/COLOR]
[COLOR=#FF7700]**finally**[/COLOR]:
    my_timer.[COLOR=black]cancel[/COLOR][COLOR=black]([/COLOR][COLOR=black])
I used the [python]("https://mindmajix.com/python/partial-functions") 3.3 it works fine.
Thank you,
Riya[/COLOR]

---

### Post by erotavlas on 2018-07-13
Thank you of your answer of course your solution works for python3.3+ as the mine.
I think I will use only python3.3+. Moreover, I modified the script in order to work for different operating system.
```

for host in tqdm(hosts):
    if platform == "linux" or platform == "darwin":
        command=["ping", "-c", "3", "-i", "0.2", host]
            timeout=0.5
        else:
            command=["ping", "-n", "1", host]
            timeout=0.2
        ping=subprocess.Popen(command,stdout=subprocess.PIPE,stderr=subprocess.PIPE)
        try:             
            [out, err]=proc.communicate(timeout=2.1)
            if proc.returncode == 0:
                if platform == "linux" or platform == "darwin":
                    avgRTT=re.search("rtt min/avg/max/mdev = (\d+.\d+)/(\d+.\d+)/(\d+.\d+)/(\d+.\d+)", str(out)).group(2)
                else:
                    # to do
                    avgRTT=re.search("", str(out))

```
Unfortunately,  windows has different ping version than GNU/linux or mac os X that does  not support the option -i and so I have to play with timeout in order  to limit the time required.
Moreover, also the parsing is different.

---

