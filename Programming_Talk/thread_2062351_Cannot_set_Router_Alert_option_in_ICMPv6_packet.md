---
title: "Cannot set Router Alert option in ICMPv6 packet"
date: 2012-09-24
forum: Programming Talk
---

### Post by shahlanuk on 2012-09-24
I am trying to to set Hop-By-Hop option in a packet before sending it out according to the example specified in Appendix C of [http://www.ietf.org/rfc/rfc3542.txt](http://www.ietf.org/rfc/rfc3542.txt) . I don’t see any errors while using the APIs but the HBH option is not set in the sent packet.
  This is my code:
  set_rtr_alert_opt (struct msghdr *msg, struct cmsghdr *cmsg)
{
    int         ralen = 0, currentlen = 0;
    void        *hbhbuf = NULL, *optp = NULL;
    u_int8_t    rtr_alert;

    rtr_alert = htons(IP6_ALERT_MLD);

    /*
     * Set the Router Alert option into the cmsg
     */
    ralen = inet6_opt_init(NULL, 0);
    if (ralen == -1) {
        return(FALSE);
    }

    ralen = inet6_opt_append(NULL, 0, ralen, IP6OPT_ROUTER_ALERT, 2,
                             2, NULL);
    if (ralen == -1) {
       return(FALSE);
    }

    ralen = inet6_opt_finish(NULL, 0, ralen);
    if (ralen == -1) {
        return(FALSE);
    }

    cmsg->cmsg_len = CMSG_LEN(ralen);
    cmsg->cmsg_level = IPPROTO_IPV6;
    cmsg->cmsg_type = IPV6_HOPOPTS;
    hbhbuf = CMSG_DATA(cmsg);
    msg->msg_controllen += ALIGN(cmsg->cmsg_len);

    currentlen = inet6_opt_init(hbhbuf, ralen);
    if (currentlen == -1) {
        return(FALSE);
    }

    currentlen = inet6_opt_append(hbhbuf, ralen, currentlen,
                                  IP6OPT_ROUTER_ALERT, 2, 2, &optp);
    if (currentlen == -1) {
        return(FALSE);
    }

    inet6_opt_set_val(optp, 0, &rtr_alert, sizeof(rtr_alert));
    currentlen = inet6_opt_finish(hbhbuf, ralen, currentlen);
    if (currentlen == -1) {
        return(FALSE);
    }

    return(TRUE);
}
  After this i call sendmsg() to send the packet out. The packet does go out but the HBH option is not present in the packet.

---

