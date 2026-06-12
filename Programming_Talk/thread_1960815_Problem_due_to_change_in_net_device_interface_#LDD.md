---
title: "Problem due to change in net_device interface #LDD"
date: 2012-04-18
forum: Programming Talk
---

### Post by harsh.C on 2012-04-18
this is the error log that i am getting:

harsh@harsh-OptiPlex-990:~/Kprog$ make
make -C /lib/modules/2.6.38-13-generic/build M=/home/harsh/Kprog modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-13-generic'
  CC [M]  /home/harsh/Kprog/kprog_4.o
/home/harsh/Kprog/kprog_4.c: In function ‘hn_init’:
/home/harsh/Kprog/kprog_4.c:402:2: error: assignment of read-only location ‘*ops’
/home/harsh/Kprog/kprog_4.c:404:2: error: assignment of read-only location ‘*ops’
/home/harsh/Kprog/kprog_4.c:405:2: error: assignment of read-only location ‘*ops’
/home/harsh/Kprog/kprog_4.c:406:5: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/harsh/Kprog/kprog_4.c:408:2: error: assignment of read-only location ‘*ops’
/home/harsh/Kprog/kprog_4.c:409:5: error: ‘struct net_device’ has no member named ‘rebuild_header’
/home/harsh/Kprog/kprog_4.c:410:5: error: ‘struct net_device’ has no member named ‘dev_hard_header’
/home/harsh/Kprog/kprog_4.c:411:2: error: assignment of read-only location ‘*ops’
/home/harsh/Kprog/kprog_4.c:415:5: error: ‘struct net_device’ has no member named ‘hard_header_cache’
make[2]: *** [/home/harsh/Kprog/kprog_4.o] Error 1
make[1]: *** [_module_/home/harsh/Kprog] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-13-generic'
make: *** [kprog_4] Error 2


i ggogled a lot and found that there has been a change in the the net_device interface, thus i tried using the net_device_ops interface but then there was this error : " assignment of read-only location ‘*ops’" . Here ops is the net_device_ops type pointer. The code for reference is :

static void hn_init(struct net_device *dev)
{	
	const struct net_device_ops *ops = dev->netdev_ops; // fix for 2.6.32
	struct hn_priv *priv;
	ether_setup(dev);
	
	ops->ndo_open=hn_open;//dev->open = hn_open;
	//-dev->release = hn_release;
	ops->ndo_stop = hn_release;
	ops->ndo_set_config=hn_config;  //dev->set_config = hn_config
	dev->hard_start_xmit =hn_tx; //this function is called to put the packet on a transmitting queue 
	//dev->do_ioctl = hn_ioctl;
	ops->ndo_get_stats= hn_stats; // dev->get_stats = hn_stats;
	dev->rebuild_header = hn_rebuild_header;
	dev->dev_hard_header = hn_header;		//creating the header added at layer 2
	ops->ndo_tx_timeout = hn_tx_timeout; //dev->tx_timeout = hn_tx_timeout;  // setting timeout for outgoing packets
	dev->watchdog_timeo = timeout;
	dev->flags	|=IFF_NOARP; // ARP (layer 2 protocol) not supported
	dev->features =NETIF_F_NO_CSUM;
	dev->hard_header_cache = NULL; // hard_header_cache is used to store the layer 2(link layer) packets temporarily,
								   //  assigning it as null prohibit caching of layer 2 packets
	priv=netdev_priv(dev);
	memset(priv,0,sizeof(struct hn_priv));
	spin_lock_init(&priv->lock);
	hn_rx_ints(dev,1);
	hn_setup_pool(dev);	
}


p|2 h3|p ..

---

