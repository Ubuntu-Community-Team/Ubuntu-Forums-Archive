---
title: "Trying to get bits out of my HID"
date: 2009-08-31
forum: Programming Talk
---

### Post by sparker256 on 2009-08-31
Here is my code and I need to get to the bit level from the packet of my HID. I am reading switches so each bit is one switch. I think I need a char to binary but so far have had no luck finding or writing one.

```
#define RECV_PACKET_LEN 2
  char packet[RECV_PACKET_LEN];

  ret = hid_get_feature_report(hid, PATH_OUT, PATHLEN, packet, RECV_PACKET_LEN);
  if (ret != HID_RET_SUCCESS) {
    fprintf(stderr, "hid_get_feature_report failed with return code %d\n", ret);
  }
```

Thanks Bill

---

### Post by smartbei on 2009-09-01
You already have the data in the required format. A char is eight bits. To isolate a single bit, use the bitwise & operator with a power of 2 representing the bit you want to test. If you want to test the bit at position a, use the & operator with 2^(a-1). To test the first (least significant bit) I would do this:
```

char mychar = something;
if (mychar & 0x1) { // 0x1 => 00000001
    printf("Bit is on");
}

```
To test the sixth bit:
```

char mychar = something;
if (mychar & 0x20) { // 0x20 => 00100000
    printf("Bit is on");
}

```
In your case, you want to test a specific bit in the packet. So to test (for example) the fifth bit in the fourth byte:
```

if (packet[3] & 0x10) { // 0x10 => 00010000
    printf("Bit is on");
}

```

---

### Post by sparker256 on 2009-09-01
> **smartbei said:**
> You already have the data in the required format. A char is eight bits. To isolate a single bit, use the bitwise & operator with a power of 2 representing the bit you want to test. If you want to test the bit at position a, use the & operator with 2^(n-1). To test the first (least significant bit) I would do this:
```

char mychar = something;
if (mychar & 0x1) { // 0x1 => 00000001
    printf("Bit is on");
}

```
To test the sixth bit:
```

char mychar = something;
if (mychar & 0x20) { // 0x40 => 00100000
    printf("Bit is on");
}

```
In your case, you want to test a specific bit in the packet. So to test (for example) the fifth bit in the fourth byte:
```

if (packet[3] & 0x10) { // 0x20 => 00010000
    printf("Bit is on");
}

```

Thank you very much that is just what I was looking for.
Bill

---

