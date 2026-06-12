---
title: "Serial port “read” operation is not working"
date: 2015-05-04
forum: Programming Talk
---

### Post by Sijith on 2015-05-04
I am trying to read data through serial port but the read operation is always returning 0.
```

// Opening COM port and m_fd returned a valid number
m_fd =  open (m_com_port, O_RDWR | O_NOCTTY | O_SYNC); 

//Read operation
length = read(m_fd, &ch, 1);  // length is always zero

setserial -g /tmp/xdl/serial/com_7 
# /tmp/xdl/serial/com_7, UART: undefined, Port: 0x0000, IRQ: 45
```

Can some one point what mistake I am doing and why setserial command gives undefined

---

