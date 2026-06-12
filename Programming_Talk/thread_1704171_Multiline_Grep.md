---
title: "Multiline Grep"
date: 2011-03-10
forum: Programming Talk
---

### Post by rohrbold on 2011-03-10
Hi,

I am currently stuck at a more or less complicated problem and hope someone may be so kind to help me out.

I'd like to analyze a protocol's behavior by means of tcpdump trace files. A decent sequence from the text export looks like this:

```

  1   0.000000     10.6.7.6 -> 224.7.7.7    GIST Query, QoS NSLP
  2   0.003707     10.6.7.7 -> 10.6.7.6     GIST Response, QoS NSLP
  3   0.004320     10.6.7.6 -> 10.6.7.7     GIST Confirm, QoS NSLP
  4   0.004442     10.6.7.6 -> 10.6.7.7     GIST Data, QoS NSLP, RESERVE
  5   0.029576     10.6.7.7 -> 10.6.7.6     GIST Data, QoS NSLP, RESPONSE
```

This happens now for some thousand runs, but every once in a while this sequence is mixed up a bit due to state refreshing data units and a sequence may look like this:


```

  1   0.000000     10.6.7.6 -> 224.7.7.7    GIST Query, QoS NSLP
  2   0.000100     10.6.7.6 -> 224.7.7.7    GIST Query, QoS NSLP
  3   0.000200     10.6.7.6 -> 224.7.7.7    GIST Query, QoS NSLP
  4   0.003707     10.6.7.7 -> 10.6.7.6     GIST Response, QoS NSLP
  5   0.004320     10.6.7.6 -> 10.6.7.7     GIST Confirm, QoS NSLP
  6   0.004442     10.6.7.6 -> 10.6.7.7     GIST Data, QoS NSLP, RESERVE
  7   0.007621     10.6.7.6 -> 10.6.7.7     GIST Data, QoS NSLP, RESERVE
  8   0.029576     10.6.7.7 -> 10.6.7.6     GIST Data, QoS NSLP, RESPONSE
```

Even though this is a valid run and I could extract the some data units manually, the data units may get mixed up too extremely after some time.
Therefore, I would like to have only those sequences extracted, that match exactly the five-tuple from the first example. You can guess that I am ultimately interested in the timestamp from the first column, but once i have a clean file, this can be easily "awked" :-)

Does anyone know of a good solution to this problem?

Thanks,
Martin

---

