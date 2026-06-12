---
title: "bluez_gatt-client"
date: 2017-06-14
forum: New to Ubuntu
---

### Post by prasanth.velliyangiri on 2017-06-14
Hi Support Team

I am creating gatt_client using blueZ in ubuntu 14.04 , i downloaded bluez 5.45 , ran some sample codes , i am able to communicate with my BLE device. my problem is sample code uses USER INTERACTION via cmd , now i want to remove this. so i edited the code bluez5.45/tools/btgatt-client.c , i am able to scan and connect to device that i want , this code uses epoll for user interaction and for other gatt related events.

[B]nfds = epoll_wait(epoll_fd, events, MAX_EPOLL_EVENTS, -1); waits for event on the fd , when i enter register-notify 0x0012 in cmd , ntfs become 2 , enents[2].events calls register-notify , gatt-client gets notification from gatt-server , now i want to make this code with out user interaction

[/B]scan
connect xx:xx:xx:xx:xx:xx
register_notify 0x0012
get data
scan 
connect to new device
...
...


int mainloop_run(void)
{

.............................
...............................

while (!epoll_terminate) {
        struct epoll_event events[MAX_EPOLL_EVENTS];
        int n, nfds;


        **nfds = epoll_wait(epoll_fd, events, MAX_EPOLL_EVENTS, -1); // this line i want to chage so code wont wait for input from user interaction**
        if (nfds < 0)
            continue;


        for (n = 0; n < nfds; n++) {
            struct mainloop_data *data = events[n].data.ptr;


            data->callback(data->fd, events[n].events,
                            data->user_data);
        }
    }
...........................
...........................


}

give some ideas.....i am not able to resolve this....


Thank you support team

---

