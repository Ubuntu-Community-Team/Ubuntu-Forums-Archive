---
title: "Source code written in which language?"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by luozhen on 2013-04-10
I am trying to read reaver 1.4 source code in ubuntu OS

After i open the file, i saw a lot code, how do i know what kind of programming language (like JAVA python) are those code written with ??????

---

### Post by layers on 2013-04-10
Can you post a sample of it,s ince I'm too lazy to go find out what you're talking about?

---

### Post by haqking on 2013-04-10
it is written in C

---

### Post by luozhen on 2013-04-11
[SIZE=2][B]For example, here is the code
please tell me in what language this code was written, thank you

By the way, please tell me how can i find out the what kind of language this is on my own???[/B][/SIZE]
```

* Reaver - 802.11 functions
 * Copyright (c) 2011, Tactical Network Solutions, Craig Heffner <cheffner@tacnetsol.com>
#include "80211.h"

/*Reads the next packet from pcap_next() and validates the FCS. */
const u_char *next_packet(struct pcap_pkthdr *header)
{
    const u_char *packet = NULL;

    /* Loop until we get a valid packet, or until we run out of packets */
    while((packet = pcap_next(get_handle(), header)) != NULL)
    {
        if(get_validate_fcs())
        {
            if(check_fcs(packet, header->len))
            {
                break;
            }
            else
            {
                cprintf(INFO, "[!] Found packet with bad FCS, skipping...\n");
            }
        }
        else
        {
            break;
        }
    }

    return packet;
}

/* 
 * Waits for a beacon packet from the target AP and populates the globule->ap_capabilities field.
 * This is used for obtaining the capabilities field and AP SSID.
 */
void read_ap_beacon()
{
        struct pcap_pkthdr header;
        const u_char *packet = NULL;
        struct radio_tap_header *rt_header = NULL;
        struct dot11_frame_header *frame_header = NULL;
        struct beacon_management_frame *beacon = NULL;
    int channel = 0;
    size_t tag_offset = 0;
    time_t start_time = 0;

    set_ap_capability(0);
    start_time = time(NULL);
    
        while(get_ap_capability() == 0)
        {
                packet = next_packet(&header);
                if(packet == NULL)
                {
                        break;
                }

                if(header.len >= MIN_BEACON_SIZE)
                {
                        rt_header = (struct radio_tap_header *) radio_header(packet, header.len);
                        frame_header = (struct dot11_frame_header *) (packet + rt_header->len);

            if(is_target(frame_header))
            {
                                if(frame_header->fc.type == MANAGEMENT_FRAME && frame_header->fc.sub_type == SUBTYPE_BEACON)
                                {
                                           beacon = (struct beacon_management_frame *) (packet + rt_header->len + sizeof(struct dot11_frame_header));
                                           set_ap_capability(beacon->capability);

                    /* Obtain the SSID and channel number from the beacon packet */
                    tag_offset = rt_header->len + sizeof(struct dot11_frame_header) + sizeof(struct beacon_management_frame);
                    channel = parse_beacon_tags(packet, header.len);
                    
                    /* If no channel was manually specified, switch to the AP's current channel */
                    if(!get_fixed_channel() && get_auto_channel_select() && channel > 0 && channel != get_channel())
                    {
                        change_channel(channel);
                        set_channel(channel);
                    }

                                           break;
                }
            }
                }

        /* If we haven't seen any beacon packets from the target within BEACON_WAIT_TIME seconds, try another channel */
        if((time(NULL) - start_time) >= BEACON_WAIT_TIME)
        {
            next_channel();
            start_time = time(NULL);
        }
        }
}
```

---

### Post by schragge on 2013-04-11
> **luozhen said:**
> please tell me how can i find out the what kind of language this is on my own?
Try this in a terminal window
```

[COLOR=green]$[/COLOR] file 80211.c
[COLOR=green]80211.c: C source, ASCII text[/COLOR]

```

---

