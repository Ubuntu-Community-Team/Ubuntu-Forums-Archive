---
title: "Bash script for usage with nagios"
date: 2011-11-10
forum: Programming Talk
---

### Post by Goldiescorpio on 2011-11-10
Hi all,

I'm using a script made by someone else.
It is used to read the CPU-usage of my Bluecoat_SG Proxy.

It works great apart from the output once implemented...

The maker suggested there might be a problem with the syntax of the logical comparison.

The code goes as follows:

```
echo $outputMessage

if [ $performanceData -ge $criticalTreshold ]; then
	exit $STATE_CRITICAL
else
	if ([ $performanceData -lt $criticalTreshold ]&&[$performanceData -ge $warningTreshold ]); then

		exit $STATE_WARNING
	else
		exit $STATE_OK
	fi
fi
```

So...my given warningTreshold is 80 (%) and my CriticalTreshold is 90 (%).

The script/plugin reads out the value...(differs but let's say in this time it is) 55% (cpu-usage).
Then it still gives me a WARNING in the output, while it should say OK.

Does anyone of you see any errors in this piece of work?

I tried ((  instead of ([  and also >= instead of -ge and so on...

Thanks in advance!

Ps. The maker states this works flawlessly on CentOS server using nagios, that why he assumes that there might be a difference in syntax between bash in CentOS and Ubuntu.


Grtz,

goldie

---

### Post by ofnuts on 2011-11-10
> **Goldiescorpio said:**
> Hi all,

I'm using a script made by someone else.
It is used to read the CPU-usage of my Bluecoat_SG Proxy.

It works great apart from the output once implemented...

The maker suggested there might be a problem with the syntax of the logical comparison.

The code goes as follows:

```
echo $outputMessage

if [ $performanceData -ge $criticalTreshold ]; then
    exit $STATE_CRITICAL
else
    if ([ $performanceData -lt $criticalTreshold ]&&[$performanceData -ge $warningTreshold ]); then

        exit $STATE_WARNING
    else
        exit $STATE_OK
    fi
fi
```So...my given warningTreshold is 80 (%) and my CriticalTreshold is 90 (%).

The script/plugin reads out the value...(differs but let's say in this time it is) 55% (cpu-usage).
Then it still gives me a WARNING in the output, while it should say OK.

Does anyone of you see any errors in this piece of work?

I tried ((  instead of ([  and also >= instead of -ge and so on...

Thanks in advance!

Ps. The maker states this works flawlessly on CentOS server using nagios, that why he assumes that there might be a difference in syntax between bash in CentOS and Ubuntu.


Grtz,

goldieHis code works for me(*) even if he is using the ksh-ish syntax. 

(*) After I fixed a syntax error: "&&[ $performanceData" instead of "&&[$performanceData", but I can't tell if it's a typo from you or if you didn't see the error because something else is hiding it (strangely, this is in the test, which, if not done, would give the results you see....)

---

### Post by ju2wheels on 2011-11-11
The double check is redundant anyway it boils down to this:

```

echo $outputMessage;

if [ $performanceData -ge $criticalTreshold ]; then
    exit $STATE_CRITICAL;
elif [ $performanceData -ge $warningTreshold ]; then
    exit $STATE_WARNING;
else
    exit $STATE_OK;
fi

```

---

### Post by Goldiescorpio on 2011-11-12
Hi,

I already want to thank you guys for your aswers.
I'll try them monday at work and report back to you.

Have a nice weekend!

Grtz

---

### Post by Goldiescorpio on 2011-11-14
Hi there,

I tested your suggestions.

@ofnuts: It was a typo on my behalf, I'm sorry. There is a space in the bash-script.

@ju2wheels: I tried your "simplified" version, but with the same result :confused:

Strange thing is...today our gataway went down so the proxy started caching...the CPU ran to 89% and then it had the status OK, while it should be warning.

So it gives warning when it should be OK and it gives OK when it should say WARNING...

:confused:

Thanks again for your efforts.

Grtz!

---

### Post by ofnuts on 2011-11-14
> **Goldiescorpio said:**
> Hi there,

I tested your suggestions.

@ofnuts: It was a typo on my behalf, I'm sorry. There is a space in the bash-script.

@ju2wheels: I tried your "simplified" version, but with the same result :confused:

Strange thing is...today our gataway went down so the proxy started caching...the CPU ran to 89% and then it had the status OK, while it should be warning.

So it gives warning when it should be OK and it gives OK when it should say WARNING...

:confused:

Thanks again for your efforts.

Grtz!ju2wheels' code works:
```

#! /bin/bash
criticalThreshold=90
warningThreshold=80
performanceData=$1

STATE_OK=0
STATE_WARNING=1
STATE_CRITICAL=2

if [ $performanceData -ge $criticalThreshold ]
then
    exit $STATE_CRITICAL;
elif [ $performanceData -ge $warningThreshold ]
then
    exit $STATE_WARNING;
else
    exit $STATE_OK;
fi

```
yields:
```

for data in {75..100};do ./testcritic $data; echo "$data: $?";done
75: 0
76: 0
77: 0
78: 0
79: 0
80: 1
81: 1
82: 1
83: 1
84: 1
85: 1
86: 1
87: 1
88: 1
89: 1
90: 2
91: 2
92: 2
93: 2
94: 2
95: 2
96: 2
97: 2
98: 2
99: 2
100: 2

```

---

### Post by Goldiescorpio on 2011-11-14
> **ofnuts said:**
> ju2wheels' code works:
```

#! /bin/bash
criticalThreshold=90
warningThreshold=80
performanceData=$1

STATE_OK=0
STATE_WARNING=1
STATE_CRITICAL=2

if [ $performanceData -ge $criticalThreshold ]
then
    exit $STATE_CRITICAL;
elif [ $performanceData -ge $warningThreshold ]
then
    exit $STATE_WARNING;
else
    exit $STATE_OK;
fi

```
yields:
```

for data in {75..100};do ./testcritic $data; echo "$data: $?";done
75: 0
76: 0
77: 0
78: 0
79: 0
80: 1
81: 1
82: 1
83: 1
84: 1
85: 1
86: 1
87: 1
88: 1
89: 1
90: 2
91: 2
92: 2
93: 2
94: 2
95: 2
96: 2
97: 2
98: 2
99: 2
100: 2

```

Hi there!

I never stated someones code did not work at all, it just did not work for me for some reason.
I found the solution, there seemed to be a problem with my utils.sh file. So nagios could not determine the nr vs. state in a correct way.

I would like to thank all of you for your input. I learned alot from it.

Thanks!

Grtz

---

