---
title: "Help with linked lists [strictly C]"
date: 2008-05-30
forum: Programming Talk
---

### Post by PandaGoat on 2008-05-30
**Background: ** Due to the lack of utilities found on windows for hosting games on Warcraft III, such as a pinger, banlist, and slot refresher, I decided to attempt to make a pinger and eventually turn it into the others also.  And yes I considered wine--and this is not the point anyway--but only a poor refresher works.  Anyway, I'm using libpcap and have everything working up to sniffing packets and storing them into structs.

**Problem: **  Every now and then a packet contains more than one "Warcraft packet" inside.  For clarity, a "Warcraft packet" is a portion inside the payload of the tcp/ip packet beginning with an identifier--either 0xFF or 0xF7--and ending at the end of the payload or when another 0xFF or 0xF7 is met.  To solve the problem of there being more than one warcraft packet, the struct to store one is a linked list.  Here is the definition of the struct:
[PHP]
typedef struct{
#define WPH_SIZE 4
  u_char type;  /* either FF(BNET) or F7(GAME) */
  u_char sig;   /* the signature of the type, like a player joined packet */
  u_char r_size[2]; /* the size of the packet in reversed order for some reason*/
} warcraft_packet_header;



struct warcraft_packet_s{
  struct warcraft_packet_s* next;
  warcraft_packet_header* header;
  u_char* data; /* the remaining part of the packet, containing the data */
};
typedef struct warcraft_packet_s warcraft_packet;
[/PHP]

When I receive a packet I construct a struct if its a warcraft packet which also tries to create a list if it contains more than one.  Here are the methods (it is not important what tcpip_packet is):
[PHP]
int construct_warcraft_packet(const tcpip_packet* packet, warcraft_packet* output)
{
  output->header = (warcraft_packet_header*)(packet->payload);
  output->data = (u_char*)(packet->payload + WPH_SIZE);
  construct_list(packet, output, packet->payload_size - WP_SIZE(output));
}

int construct_list(const tcpip_packet* packet, warcraft_packet* wp, u_short size_left)
{
  if(size_left == 0)
    {
      wp->next = NULL;
      return 0;
    }

  wp->next->header = (warcraft_packet_header*)(packet->payload + WP_SIZE(wp));
  wp->next->data = (u_char*)(packet->payload + WP_SIZE(wp) + WPH_SIZE);
  construct_list(packet, wp->next, size_left - WP_SIZE(wp));
}
[/PHP]
The payload is a pointer to the place is memory the payload starts.

The problem is in construct_list. I'm not implementing a linked list correctly.  When the program gets to this part is gets a segmentation fault, and I believe it constructs the second element in the list properly then seg faults on the next (in each test, it appears to construct the linked list correctly up to the first next, then on wp->next->next is seg faults). And yes everything is correctly working except constructing the linked lists. **So for the "not enough info" people: the only problem is how I implement linked lists so check the last section and see if its correct; if it is correct, then it is a problem I have to deal with because there is too much to add to this already large post, or I can email you everything if you feel like helping**.

Thank you.

---

### Post by geirha on 2008-05-30
if size_left is 0 you set wp->next to NULL, which is good, but if size_left is greater than zero, you don't point wp->next to anything. wp->next is thus undefined, and then you do wp->next->header = ...

---

