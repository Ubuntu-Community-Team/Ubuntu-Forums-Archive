---
title: "undefined reference while linking ns2"
date: 2012-06-19
forum: Programming Talk
---

### Post by hasanalikhattak on 2012-06-19
i have added a module to ns2 and i am compiling it when i get undefined reference error. 

```
g++ -lneoclassic -lrt -lxml2 -o ns \
    		common/tclAppInit.o  tools/random.o tools/rng.o tools/ranvar.o common/misc.o common/timer-handler.o common/scheduler.o common/object.o common/packet.o common/ip.o routing/route.o common/connector.o common/ttl.o trace/trace.o trace/trace-ip.o classifier/classifier.o classifier/classifier-addr.o classifier/classifier-hash.o classifier/classifier-virtual.o classifier/classifier-mcast.o classifier/classifier-bst.o classifier/classifier-mpath.o mcast/replicator.o classifier/classifier-mac.o classifier/classifier-qs.o classifier/classifier-port.o src_rtg/classifier-sr.o src_rtg/sragent.o src_rtg/hdr_src.o adc/ump.o qs/qsagent.o qs/hdr_qs.o apps/app.o apps/telnet.o tcp/tcplib-telnet.o tools/trafgen.o trace/traffictrace.o tools/pareto.o tools/expoo.o tools/cbr_traffic.o adc/tbf.o adc/resv.o adc/sa.o tcp/saack.o tools/measuremod.o adc/estimator.o adc/adc.o adc/ms-adc.o adc/timewindow-est.o adc/acto-adc.o adc/pointsample-est.o adc/salink.o adc/actp-adc.o adc/hb-adc.o adc/expavg-est.o adc/param-adc.o adc/null-estimator.o adc/adaptive-receiver.o apps/vatrcvr.o adc/consrcvr.o common/agent.o common/message.o apps/udp.o common/session-rtp.o apps/rtp.o tcp/rtcp.o common/ivs.o common/messpass.o common/tp.o common/tpm.o apps/worm.o tcp/tcp.o tcp/tcp-sink.o tcp/tcp-reno.o tcp/tcp-newreno.o tcp/tcp-vegas.o tcp/tcp-rbp.o tcp/tcp-full.o tcp/rq.o baytcp/tcp-full-bay.o baytcp/ftpc.o baytcp/ftps.o tcp/scoreboard.o tcp/scoreboard-rq.o tcp/tcp-sack1.o tcp/tcp-fack.o tcp/tcp-asym.o tcp/tcp-asym-sink.o tcp/tcp-fs.o tcp/tcp-asym-fs.o tcp/tcp-int.o tcp/chost.o tcp/tcp-session.o tcp/nilist.o sctp/sctp.o apps/sctp_app1.o sctp/sctp-timestamp.o sctp/sctp-hbAfterRto.o sctp/sctp-multipleFastRtx.o sctp/sctp-mfrHbAfterRto.o sctp/sctp-mfrTimestamp.o sctp/sctp-cmt.o sctp/sctpDebug.o tools/integrator.o tools/queue-monitor.o tools/flowmon.o tools/loss-monitor.o queue/queue.o queue/drop-tail.o adc/simple-intserv-sched.o queue/red.o queue/semantic-packetqueue.o queue/semantic-red.o tcp/ack-recons.o queue/sfq.o queue/fq.o queue/drr.o queue/srr.o queue/cbq.o queue/jobs.o queue/marker.o queue/demarker.o link/hackloss.o queue/errmodel.o queue/fec.o link/delay.o tcp/snoop.o gaf/gaf.o link/dynalink.o routing/rtProtoDV.o common/net-interface.o mcast/ctrMcast.o mcast/mcast_ctrl.o mcast/srm.o common/sessionhelper.o queue/delaymodel.o mcast/srm-ssm.o mcast/srm-topo.o routing/alloc-address.o routing/address.o lib/int.Vec.o lib/int.RVec.o lib/dmalloc_support.o webcache/http.o webcache/tcp-simple.o webcache/pagepool.o webcache/inval-agent.o webcache/tcpapp.o webcache/http-aux.o webcache/mcache.o webcache/webtraf.o webcache/webserver.o webcache/logweb.o empweb/empweb.o empweb/empftp.o realaudio/realaudio.o mac/lanRouter.o classifier/filter.o common/pkt-counter.o common/Decapsulator.o common/Encapsulator.o common/encap.o mac/channel.o mac/mac.o mac/ll.o mac/mac-802_11.o mac/mac-802_3.o mac/mac-tdma.o mac/smac.o mobile/mip.o mobile/mip-reg.o mobile/gridkeeper.o mobile/propagation.o mobile/tworayground.o mobile/antenna.o mobile/omni-antenna.o mobile/shadowing.o mobile/shadowing-vis.o mobile/dumb-agent.o common/bi-connector.o common/node.o common/mobilenode.o mac/arp.o mobile/god.o mobile/dem.o mobile/topography.o mobile/modulation.o queue/priqueue.o queue/dsr-priqueue.o mac/phy.o mac/wired-phy.o mac/wireless-phy.o mac/mac-timers.o trace/cmu-trace.o mac/varp.o mac/mac-simple.o satellite/sat-hdlc.o dsdv/dsdv.o dsdv/rtable.o queue/rtqueue.o routing/rttable.o imep/imep.o imep/dest_queue.o imep/imep_api.o imep/imep_rt.o imep/rxmit_queue.o imep/imep_timers.o imep/imep_util.o imep/imep_io.o tora/tora.o tora/tora_api.o tora/tora_dest.o tora/tora_io.o tora/tora_logs.o tora/tora_neighbor.o dsr/dsragent.o dsr/hdr_sr.o dsr/mobicache.o dsr/path.o dsr/requesttable.o dsr/routecache.o dsr/add_sr.o dsr/dsr_proto.o dsr/flowstruct.o dsr/linkcache.o dsr/simplecache.o dsr/sr_forwarder.o aodv/aodv_logs.o aodv/aodv.o aodv/aodv_rtable.o aodv/aodv_rqueue.o common/ns-process.o satellite/satgeometry.o satellite/sathandoff.o satellite/satlink.o satellite/satnode.o satellite/satposition.o satellite/satroute.o satellite/sattrace.o rap/raplist.o rap/rap.o rap/media-app.o rap/utilities.o common/fsm.o tcp/tcp-abs.o diffusion/diffusion.o diffusion/diff_rate.o diffusion/diff_prob.o diffusion/diff_sink.o diffusion/flooding.o diffusion/omni_mcast.o diffusion/hash_table.o diffusion/routing_table.o diffusion/iflist.o tcp/tfrc.o tcp/tfrc-sink.o mobile/energy-model.o apps/ping.o tcp/tcp-rfc793edu.o queue/rio.o queue/semantic-rio.o tcp/tcp-sack-rh.o tcp/scoreboard-rh.o plm/loss-monitor-plm.o plm/cbr-traffic-PP.o linkstate/hdr-ls.o mpls/classifier-addr-mpls.o mpls/ldp.o mpls/mpls-module.o routing/rtmodule.o classifier/classifier-hier.o routing/addr-params.o nix/hdr_nv.o nix/classifier-nix.o nix/nixnode.o routealgo/rnode.o routealgo/bfs.o routealgo/rbitmap.o routealgo/rlookup.o routealgo/routealgo.o nix/nixvec.o nix/nixroute.o diffserv/dsred.o diffserv/dsredq.o diffserv/dsEdge.o diffserv/dsCore.o diffserv/dsPolicy.o diffserv/ew.o diffserv/dewp.o queue/red-pd.o queue/pi.o queue/vq.o queue/rem.o queue/gk.o pushback/rate-limit.o pushback/rate-limit-strategy.o pushback/ident-tree.o pushback/agg-spec.o pushback/logging-data-struct.o pushback/rate-estimator.o pushback/pushback-queue.o pushback/pushback.o common/parentnode.o trace/basetrace.o common/simulator.o asim/asim.o common/scheduler-map.o common/splay-scheduler.o linkstate/ls.o linkstate/rtProtoLS.o pgm/classifier-pgm.o pgm/pgm-agent.o pgm/pgm-sender.o pgm/pgm-receiver.o mcast/rcvbuf.o mcast/classifier-lms.o mcast/lms-agent.o mcast/lms-receiver.o mcast/lms-sender.o queue/delayer.o xcp/xcpq.o xcp/xcp.o xcp/xcp-end-sys.o wpan/p802_15_4csmaca.o wpan/p802_15_4fail.o wpan/p802_15_4hlist.o wpan/p802_15_4mac.o wpan/p802_15_4nam.o wpan/p802_15_4phy.o wpan/p802_15_4sscs.o wpan/p802_15_4timer.o wpan/p802_15_4trace.o wpan/p802_15_4transac.o maser/maser.o maser/mamas.o diffusion3/lib/nr/nr.o diffusion3/lib/dr.o diffusion3/filters/diffusion/one_phase_pull.o diffusion3/filters/diffusion/two_phase_pull.o diffusion3/lib/diffapp.o diffusion3/ns/diffagent.o diffusion3/ns/diffrtg.o diffusion3/ns/difftimer.o diffusion3/filter_core/filter_core.o diffusion3/filter_core/iolog.o diffusion3/filter_core/iostats.o diffusion3/lib/main/attrs.o diffusion3/lib/main/events.o diffusion3/lib/main/iodev.o diffusion3/lib/main/iohook.o diffusion3/lib/main/timers.o diffusion3/lib/main/message.o diffusion3/lib/main/tools.o diffusion3/apps/gear_examples/gear_common.o diffusion3/apps/gear_examples/gear_receiver.o diffusion3/apps/gear_examples/gear_sender.o diffusion3/apps/rmst_examples/rmst_sink.o diffusion3/apps/rmst_examples/rmst_source.o diffusion3/apps/ping/1pp_ping_sender.o diffusion3/apps/ping/1pp_ping_receiver.o diffusion3/apps/ping/2pp_ping_sender.o diffusion3/apps/ping/2pp_ping_receiver.o diffusion3/apps/ping/ping_common.o diffusion3/apps/ping/push_receiver.o diffusion3/apps/ping/push_sender.o diffusion3/filters/gear/gear_attr.o diffusion3/filters/gear/gear.o diffusion3/filters/gear/gear_tools.o diffusion3/filters/misc/log.o diffusion3/filters/misc/srcrt.o diffusion3/filters/misc/tag.o diffusion3/filters/rmst/rmst.o diffusion3/filters/rmst/rmst_filter.o delaybox/delaybox.o packmime/packmime_HTTP.o packmime/packmime_HTTP_rng.o packmime/packmime_OL.o packmime/packmime_OL_ranvar.o packmime/packmime_ranvar.o gen/version.o gen/ns_tcl.o gen/ptypes.o  common/win32.o -L/usr/local/lib -ltclcl -L/usr/local/lib -lotcl -L/usr/local/lib -ltk8.4 -L/usr/local/lib -ltcl8.4 -lXext -lX11 -lnsl -ldl -lm
    maser/mamas.o: In function `mamasReasoner::mamasReasoner()':
    mamas.cc:(.text+0x95): undefined reference to `NeoEnvironment::initFromNs(std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, int)'
    maser/mamas.o: In function `mamasReasoner::build_ontology_tree(knBase&)':
    mamas.cc:(.text+0x1c4c): undefined reference to `clock_getcpuclockid'
    mamas.cc:(.text+0x1c76): undefined reference to `clock_gettime'
    mamas.cc:(.text+0x1c84): undefined reference to `NeoEnvironment::evaluateCommand(String const&)'
    mamas.cc:(.text+0x1c99): undefined reference to `clock_gettime'
    maser/mamas.o: In function `NeoEnvironment::readXmlFromMemory(char const*, char const*)':
    mamas.cc:(.text._ZN14NeoEnvironment17readXmlFromMemoryEPKcS1_[NeoEnvironment::readXmlFromMemory(char const*, char const*)]+0x14): undefined reference to `Parser::readXmlFromMemory(char const*, char const*)'
    
    collect2: ld returned 1 exit status
    make: *** [ns] Error 1
```
the library which it is asking for is present at the > /usr/local/lib/libneoclassic.so and the makefile can be seen here [http://pastebin.com/NZWPxKht]("http://pastebin.com/NZWPxKht")
which use the following code for linking.

```
    LINK    = g++
    LDFLAGS =  -lneoclassic -lrt -lxml2
    LDOUT   = -o $(BLANK)
    LIB     = \
            -L/usr/local/lib -ltclcl -L/usr/local/lib -lotcl -L/usr/local/lib -ltk8.4 -L/usr/local/lib -ltcl8.4 \
            -lXext -lX11 \
             -lnsl -ldl \
            -lm -lm
    OBJ_CC = \
            tools/random.o tools/rng.o tools/ranvar.o common/misc.o common/timer-handler.o \
            common/scheduler.o common/object.o common/packet.o \
            common/ip.o routing/route.o common/connector.o common/ttl.o \
            trace/trace.o trace/trace-ip.o \
            classifier/classifier.o classifier/classifier-addr.o \
            classifier/classifier-hash.o \
            classifier/classifier-virtual.o \
            classifier/classifier-mcast.o \
            classifier/classifier-bst.o \
            classifier/classifier-mpath.o mcast/replicator.o \
            classifier/classifier-mac.o \
            classifier/classifier-qs.o \
            classifier/classifier-port.o src_rtg/classifier-sr.o \
            src_rtg/sragent.o src_rtg/hdr_src.o adc/ump.o \
            qs/qsagent.o qs/hdr_qs.o \
            apps/app.o apps/telnet.o tcp/tcplib-telnet.o \
            tools/trafgen.o trace/traffictrace.o tools/pareto.o \
            tools/expoo.o tools/cbr_traffic.o \
            adc/tbf.o adc/resv.o adc/sa.o tcp/saack.o \
            tools/measuremod.o adc/estimator.o adc/adc.o adc/ms-adc.o \
            adc/timewindow-est.o adc/acto-adc.o \
            adc/pointsample-est.o adc/salink.o adc/actp-adc.o \
            adc/hb-adc.o adc/expavg-est.o\
            adc/param-adc.o adc/null-estimator.o \
            adc/adaptive-receiver.o apps/vatrcvr.o adc/consrcvr.o \
            common/agent.o common/message.o apps/udp.o \
            common/session-rtp.o apps/rtp.o tcp/rtcp.o \
            common/ivs.o \
            common/messpass.o common/tp.o common/tpm.o apps/worm.o \
            tcp/tcp.o tcp/tcp-sink.o tcp/tcp-reno.o \
            tcp/tcp-newreno.o \
            tcp/tcp-vegas.o tcp/tcp-rbp.o tcp/tcp-full.o tcp/rq.o \
            baytcp/tcp-full-bay.o baytcp/ftpc.o baytcp/ftps.o \
            tcp/scoreboard.o tcp/scoreboard-rq.o tcp/tcp-sack1.o tcp/tcp-fack.o \
            tcp/tcp-asym.o tcp/tcp-asym-sink.o tcp/tcp-fs.o \
            tcp/tcp-asym-fs.o \
            tcp/tcp-int.o tcp/chost.o tcp/tcp-session.o \
            tcp/nilist.o \
            sctp/sctp.o apps/sctp_app1.o\
            sctp/sctp-timestamp.o sctp/sctp-hbAfterRto.o \
            sctp/sctp-multipleFastRtx.o sctp/sctp-mfrHbAfterRto.o \
            sctp/sctp-mfrTimestamp.o \
            sctp/sctp-cmt.o \
            sctp/sctpDebug.o \
            tools/integrator.o tools/queue-monitor.o \
            tools/flowmon.o tools/loss-monitor.o \
            queue/queue.o queue/drop-tail.o \
            adc/simple-intserv-sched.o queue/red.o \
            queue/semantic-packetqueue.o queue/semantic-red.o \
            tcp/ack-recons.o \
            queue/sfq.o queue/fq.o queue/drr.o queue/srr.o queue/cbq.o \
            queue/jobs.o queue/marker.o queue/demarker.o \
            link/hackloss.o queue/errmodel.o queue/fec.o\
            link/delay.o tcp/snoop.o \
            gaf/gaf.o \
            link/dynalink.o routing/rtProtoDV.o common/net-interface.o \
            mcast/ctrMcast.o mcast/mcast_ctrl.o mcast/srm.o \
            common/sessionhelper.o queue/delaymodel.o \
            mcast/srm-ssm.o mcast/srm-topo.o \
            routing/alloc-address.o routing/address.o \
            $(LIB_DIR)int.Vec.o $(LIB_DIR)int.RVec.o \
            $(LIB_DIR)dmalloc_support.o \
            webcache/http.o webcache/tcp-simple.o webcache/pagepool.o \
            webcache/inval-agent.o webcache/tcpapp.o webcache/http-aux.o \
            webcache/mcache.o webcache/webtraf.o \
            webcache/webserver.o \
            webcache/logweb.o \
            empweb/empweb.o \
            empweb/empftp.o \
            realaudio/realaudio.o \
            mac/lanRouter.o classifier/filter.o \
            common/pkt-counter.o \
            common/Decapsulator.o common/Encapsulator.o \
            common/encap.o \
            mac/channel.o mac/mac.o mac/ll.o mac/mac-802_11.o \
            mac/mac-802_3.o mac/mac-tdma.o mac/smac.o \
            mobile/mip.o mobile/mip-reg.o mobile/gridkeeper.o \
            mobile/propagation.o mobile/tworayground.o \
            mobile/antenna.o mobile/omni-antenna.o \
            mobile/shadowing.o mobile/shadowing-vis.o mobile/dumb-agent.o \
            common/bi-connector.o common/node.o \
            common/mobilenode.o \
            mac/arp.o mobile/god.o mobile/dem.o \
            mobile/topography.o mobile/modulation.o \
            queue/priqueue.o queue/dsr-priqueue.o \
            mac/phy.o mac/wired-phy.o mac/wireless-phy.o \
            mac/mac-timers.o trace/cmu-trace.o mac/varp.o \
            mac/mac-simple.o \
            satellite/sat-hdlc.o \
            dsdv/dsdv.o dsdv/rtable.o queue/rtqueue.o \
            routing/rttable.o \
            imep/imep.o imep/dest_queue.o imep/imep_api.o \
            imep/imep_rt.o imep/rxmit_queue.o imep/imep_timers.o \
            imep/imep_util.o imep/imep_io.o \
            tora/tora.o tora/tora_api.o tora/tora_dest.o \
            tora/tora_io.o tora/tora_logs.o tora/tora_neighbor.o \
            dsr/dsragent.o dsr/hdr_sr.o dsr/mobicache.o dsr/path.o \
            dsr/requesttable.o dsr/routecache.o dsr/add_sr.o \
            dsr/dsr_proto.o dsr/flowstruct.o dsr/linkcache.o \
            dsr/simplecache.o dsr/sr_forwarder.o \
            aodv/aodv_logs.o aodv/aodv.o \
            aodv/aodv_rtable.o aodv/aodv_rqueue.o \
            common/ns-process.o \
            satellite/satgeometry.o satellite/sathandoff.o \
            satellite/satlink.o satellite/satnode.o \
            satellite/satposition.o satellite/satroute.o \
            satellite/sattrace.o \
            rap/raplist.o rap/rap.o rap/media-app.o rap/utilities.o \
            common/fsm.o tcp/tcp-abs.o \
            diffusion/diffusion.o diffusion/diff_rate.o diffusion/diff_prob.o \
            diffusion/diff_sink.o diffusion/flooding.o diffusion/omni_mcast.o \
            diffusion/hash_table.o diffusion/routing_table.o diffusion/iflist.o \
            tcp/tfrc.o tcp/tfrc-sink.o mobile/energy-model.o apps/ping.o tcp/tcp-rfc793edu.o \
            queue/rio.o queue/semantic-rio.o tcp/tcp-sack-rh.o tcp/scoreboard-rh.o \
            plm/loss-monitor-plm.o plm/cbr-traffic-PP.o \
            linkstate/hdr-ls.o \
            mpls/classifier-addr-mpls.o mpls/ldp.o mpls/mpls-module.o \
            routing/rtmodule.o classifier/classifier-hier.o \
            routing/addr-params.o \
             nix/hdr_nv.o nix/classifier-nix.o \
             nix/nixnode.o \
             routealgo/rnode.o \
             routealgo/bfs.o \
             routealgo/rbitmap.o \
             routealgo/rlookup.o \
             routealgo/routealgo.o \
             nix/nixvec.o \
            nix/nixroute.o \
            diffserv/dsred.o diffserv/dsredq.o \
            diffserv/dsEdge.o diffserv/dsCore.o \
            diffserv/dsPolicy.o diffserv/ew.o diffserv/dewp.o \
            queue/red-pd.o queue/pi.o queue/vq.o queue/rem.o \
            queue/gk.o \
            pushback/rate-limit.o pushback/rate-limit-strategy.o \
            pushback/ident-tree.o pushback/agg-spec.o \
            pushback/logging-data-struct.o \
            pushback/rate-estimator.o \
            pushback/pushback-queue.o pushback/pushback.o \
            common/parentnode.o trace/basetrace.o \
            common/simulator.o asim/asim.o \
            common/scheduler-map.o common/splay-scheduler.o \
            linkstate/ls.o linkstate/rtProtoLS.o \
            pgm/classifier-pgm.o pgm/pgm-agent.o pgm/pgm-sender.o \
            pgm/pgm-receiver.o mcast/rcvbuf.o \
            mcast/classifier-lms.o mcast/lms-agent.o mcast/lms-receiver.o \
            mcast/lms-sender.o \
            queue/delayer.o \
            xcp/xcpq.o xcp/xcp.o xcp/xcp-end-sys.o \
            wpan/p802_15_4csmaca.o wpan/p802_15_4fail.o \
            wpan/p802_15_4hlist.o wpan/p802_15_4mac.o \
            wpan/p802_15_4nam.o wpan/p802_15_4phy.o \
            wpan/p802_15_4sscs.o wpan/p802_15_4timer.o \
            wpan/p802_15_4trace.o wpan/p802_15_4transac.o \
            maser/maser.o maser/mamas.o \
            $(OBJ_STL)
    
    $(LINK) $(LDFLAGS) $(LDOUT)$@ \
                        common/tclAppInit.o $(OBJ) $(LIB)
```

---

### Post by dwhitney67 on 2012-06-19
I do not know if the following will fix the issue you are having, but the following are *not* LDFLAGS:
```

LDFLAGS =  -lneoclassic -lrt

```
Those are references to libraries, and thus should be added to your LIB declaration.  An option that begins with a -L can be construed to be an LDFLAG, but not those with a lower-case l.

Btw, there are easier ways to build a collection of s/w modules, that does not involve listing each and every module in the Makefile.

I would be curious if the following Makefile would be helpful to you:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

DEBUG    = -g
INCLUDES = 

CXXFLAGS = $(DEBUG) -Wall -pedantic $(INCLUDES) -c

LDFLAGS  = -L/usr/local/lib
LIBS     = -ltclcl -lotcl -ltk8.4 -ltcl8.4 -lXext -lX11 -lnsl -ldl -lm -lm -lneoclassic -lrt

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL    = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(APP)

$(APP): $(OBJS)
        $(CXX) $(LDFLAGS) $^ $(LIBS) -o $@

$(OBJDIR)/%.o: %.cpp
        $(CXX) $(CXXFLAGS) $(DEPENDS) $< -o $@

clean:
        $(RM) -r $(OBJDIR)

distclean: clean
        $(RM) $(APP)

buildrepo:
        @$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
        mkdir -p $(OBJDIR)/$$dir; \
   done
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```
You will need to specify where your header files are located at by defining INCLUDES.  For example:
```

INCLUDES = -I./includes

```

---

### Post by hasanalikhattak on 2012-06-19
i think the same but these are in the NS2 code so might be some old convention that is still followed. but after adding the library -lxml2 i was able to reduce some of the errors.
now i have only these
```
g++ -lneoclassic -lrt -lxml2 -o ns \
maser/mamas.o: In function `mamasReasoner::mamasReasoner()':
mamas.cc:(.text+0x95): undefined reference to `NeoEnvironment::initFromNs(std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, int)'
maser/mamas.o: In function `mamasReasoner::build_ontology_tree(knBase&)':
mamas.cc:(.text+0x1c4c): undefined reference to `clock_getcpuclockid'
mamas.cc:(.text+0x1c76): undefined reference to `clock_gettime'
mamas.cc:(.text+0x1c84): undefined reference to `NeoEnvironment::evaluateCommand(String const&)'
mamas.cc:(.text+0x1c99): undefined reference to `clock_gettime'
maser/mamas.o: In function `NeoEnvironment::readXmlFromMemory(char const*, char const*)':
mamas.cc:(.text._ZN14NeoEnvironment17readXmlFromMemoryEPKcS1_[NeoEnvironment::readXmlFromMemory(char const*, char const*)]+0x14): undefined reference to `Parser::readXmlFromMemory(char const*, char const*)'
collect2: ld returned 1 exit status
make: *** [ns] Error 1
```

> **dwhitney67 said:**
> I do not know if the following will fix the issue you are having, but the following are *not* LDFLAGS:
```

LDFLAGS =  -lneoclassic -lrt

```
Those are references to libraries, and thus should be added to your LIB declaration.  An option that begins with a -L can be construed to be an LDFLAG, but not those with a lower-case l.

Btw, there are easier ways to build a collection of s/w modules, that does not involve listing each and every module in the Makefile.

I would be curious if the following Makefile would be helpful to you:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

DEBUG    = -g
INCLUDES = 

CXXFLAGS = $(DEBUG) -Wall -pedantic $(INCLUDES) -c

LDFLAGS  = -L/usr/local/lib
LIBS     = -ltclcl -lotcl -ltk8.4 -ltcl8.4 -lXext -lX11 -lnsl -ldl -lm -lm -lneoclassic -lrt

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL    = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(APP)

$(APP): $(OBJS)
        $(CXX) $(LDFLAGS) $^ $(LIBS) -o $@

$(OBJDIR)/%.o: %.cpp
        $(CXX) $(CXXFLAGS) $(DEPENDS) $< -o $@

clean:
        $(RM) -r $(OBJDIR)

distclean: clean
        $(RM) $(APP)

buildrepo:
        @$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
        mkdir -p $(OBJDIR)/$$dir; \
   done
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```
You will need to specify where your header files are located at by defining INCLUDES.  For example:
```

INCLUDES = -I./includes

```

---

### Post by dwhitney67 on 2012-06-19
It is critical that you learn to read if you want to advance in your studies.  Hmmm, perhaps I was not clear before...

The libraries need to be specified *after *your object files, not before.

For example, this statement is wrong:
```

g++ -lrt MyModule.o -o myprog

```
This one is correct:
```

g++ MyModule.o -lrt -o myprog

```
Note the ordering of the object file versus the library specification.

If you remove the library specifications from LDFLAGS and place them with LIB, then your build issues should be resolved.

---

### Post by hasanalikhattak on 2012-06-19
thank you i was able to solve that using your suggestion. but i have one error remaining
```
g++ -lneoclassic -lxml2 -o ns \
		common/tclAppInit.o  tools/random.o tools/rng.o tools/ranvar.o common/misc.o common/timer-handler.o common/scheduler.o common/object.o common/packet.o common/ip.o routing/route.o common/connector.o common/ttl.o trace/trace.o trace/trace-ip.o classifier/classifier.o classifier/classifier-addr.o classifier/classifier-hash.o classifier/classifier-virtual.o classifier/classifier-mcast.o classifier/classifier-bst.o classifier/classifier-mpath.o mcast/replicator.o classifier/classifier-mac.o classifier/classifier-qs.o classifier/classifier-port.o src_rtg/classifier-sr.o src_rtg/sragent.o src_rtg/hdr_src.o adc/ump.o qs/qsagent.o qs/hdr_qs.o apps/app.o apps/telnet.o tcp/tcplib-telnet.o tools/trafgen.o trace/traffictrace.o tools/pareto.o tools/expoo.o tools/cbr_traffic.o adc/tbf.o adc/resv.o adc/sa.o tcp/saack.o tools/measuremod.o adc/estimator.o adc/adc.o adc/ms-adc.o adc/timewindow-est.o adc/acto-adc.o adc/pointsample-est.o adc/salink.o adc/actp-adc.o adc/hb-adc.o adc/expavg-est.o adc/param-adc.o adc/null-estimator.o adc/adaptive-receiver.o apps/vatrcvr.o adc/consrcvr.o common/agent.o common/message.o apps/udp.o common/session-rtp.o apps/rtp.o tcp/rtcp.o common/ivs.o common/messpass.o common/tp.o common/tpm.o apps/worm.o tcp/tcp.o tcp/tcp-sink.o tcp/tcp-reno.o tcp/tcp-newreno.o tcp/tcp-vegas.o tcp/tcp-rbp.o tcp/tcp-full.o tcp/rq.o baytcp/tcp-full-bay.o baytcp/ftpc.o baytcp/ftps.o tcp/scoreboard.o tcp/scoreboard-rq.o tcp/tcp-sack1.o tcp/tcp-fack.o tcp/tcp-asym.o tcp/tcp-asym-sink.o tcp/tcp-fs.o tcp/tcp-asym-fs.o tcp/tcp-int.o tcp/chost.o tcp/tcp-session.o tcp/nilist.o sctp/sctp.o apps/sctp_app1.o sctp/sctp-timestamp.o sctp/sctp-hbAfterRto.o sctp/sctp-multipleFastRtx.o sctp/sctp-mfrHbAfterRto.o sctp/sctp-mfrTimestamp.o sctp/sctp-cmt.o sctp/sctpDebug.o tools/integrator.o tools/queue-monitor.o tools/flowmon.o tools/loss-monitor.o queue/queue.o queue/drop-tail.o adc/simple-intserv-sched.o queue/red.o queue/semantic-packetqueue.o queue/semantic-red.o tcp/ack-recons.o queue/sfq.o queue/fq.o queue/drr.o queue/srr.o queue/cbq.o queue/jobs.o queue/marker.o queue/demarker.o link/hackloss.o queue/errmodel.o queue/fec.o link/delay.o tcp/snoop.o gaf/gaf.o link/dynalink.o routing/rtProtoDV.o common/net-interface.o mcast/ctrMcast.o mcast/mcast_ctrl.o mcast/srm.o common/sessionhelper.o queue/delaymodel.o mcast/srm-ssm.o mcast/srm-topo.o routing/alloc-address.o routing/address.o lib/int.Vec.o lib/int.RVec.o lib/dmalloc_support.o webcache/http.o webcache/tcp-simple.o webcache/pagepool.o webcache/inval-agent.o webcache/tcpapp.o webcache/http-aux.o webcache/mcache.o webcache/webtraf.o webcache/webserver.o webcache/logweb.o empweb/empweb.o empweb/empftp.o realaudio/realaudio.o mac/lanRouter.o classifier/filter.o common/pkt-counter.o common/Decapsulator.o common/Encapsulator.o common/encap.o mac/channel.o mac/mac.o mac/ll.o mac/mac-802_11.o mac/mac-802_3.o mac/mac-tdma.o mac/smac.o mobile/mip.o mobile/mip-reg.o mobile/gridkeeper.o mobile/propagation.o mobile/tworayground.o mobile/antenna.o mobile/omni-antenna.o mobile/shadowing.o mobile/shadowing-vis.o mobile/dumb-agent.o common/bi-connector.o common/node.o common/mobilenode.o mac/arp.o mobile/god.o mobile/dem.o mobile/topography.o mobile/modulation.o queue/priqueue.o queue/dsr-priqueue.o mac/phy.o mac/wired-phy.o mac/wireless-phy.o mac/mac-timers.o trace/cmu-trace.o mac/varp.o mac/mac-simple.o satellite/sat-hdlc.o dsdv/dsdv.o dsdv/rtable.o queue/rtqueue.o routing/rttable.o imep/imep.o imep/dest_queue.o imep/imep_api.o imep/imep_rt.o imep/rxmit_queue.o imep/imep_timers.o imep/imep_util.o imep/imep_io.o tora/tora.o tora/tora_api.o tora/tora_dest.o tora/tora_io.o tora/tora_logs.o tora/tora_neighbor.o dsr/dsragent.o dsr/hdr_sr.o dsr/mobicache.o dsr/path.o dsr/requesttable.o dsr/routecache.o dsr/add_sr.o dsr/dsr_proto.o dsr/flowstruct.o dsr/linkcache.o dsr/simplecache.o dsr/sr_forwarder.o aodv/aodv_logs.o aodv/aodv.o aodv/aodv_rtable.o aodv/aodv_rqueue.o common/ns-process.o satellite/satgeometry.o satellite/sathandoff.o satellite/satlink.o satellite/satnode.o satellite/satposition.o satellite/satroute.o satellite/sattrace.o rap/raplist.o rap/rap.o rap/media-app.o rap/utilities.o common/fsm.o tcp/tcp-abs.o diffusion/diffusion.o diffusion/diff_rate.o diffusion/diff_prob.o diffusion/diff_sink.o diffusion/flooding.o diffusion/omni_mcast.o diffusion/hash_table.o diffusion/routing_table.o diffusion/iflist.o tcp/tfrc.o tcp/tfrc-sink.o mobile/energy-model.o apps/ping.o tcp/tcp-rfc793edu.o queue/rio.o queue/semantic-rio.o tcp/tcp-sack-rh.o tcp/scoreboard-rh.o plm/loss-monitor-plm.o plm/cbr-traffic-PP.o linkstate/hdr-ls.o mpls/classifier-addr-mpls.o mpls/ldp.o mpls/mpls-module.o routing/rtmodule.o classifier/classifier-hier.o routing/addr-params.o nix/hdr_nv.o nix/classifier-nix.o nix/nixnode.o routealgo/rnode.o routealgo/bfs.o routealgo/rbitmap.o routealgo/rlookup.o routealgo/routealgo.o nix/nixvec.o nix/nixroute.o diffserv/dsred.o diffserv/dsredq.o diffserv/dsEdge.o diffserv/dsCore.o diffserv/dsPolicy.o diffserv/ew.o diffserv/dewp.o queue/red-pd.o queue/pi.o queue/vq.o queue/rem.o queue/gk.o pushback/rate-limit.o pushback/rate-limit-strategy.o pushback/ident-tree.o pushback/agg-spec.o pushback/logging-data-struct.o pushback/rate-estimator.o pushback/pushback-queue.o pushback/pushback.o common/parentnode.o trace/basetrace.o common/simulator.o asim/asim.o common/scheduler-map.o common/splay-scheduler.o linkstate/ls.o linkstate/rtProtoLS.o pgm/classifier-pgm.o pgm/pgm-agent.o pgm/pgm-sender.o pgm/pgm-receiver.o mcast/rcvbuf.o mcast/classifier-lms.o mcast/lms-agent.o mcast/lms-receiver.o mcast/lms-sender.o queue/delayer.o xcp/xcpq.o xcp/xcp.o xcp/xcp-end-sys.o wpan/p802_15_4csmaca.o wpan/p802_15_4fail.o wpan/p802_15_4hlist.o wpan/p802_15_4mac.o wpan/p802_15_4nam.o wpan/p802_15_4phy.o wpan/p802_15_4sscs.o wpan/p802_15_4timer.o wpan/p802_15_4trace.o wpan/p802_15_4transac.o maser/maser.o maser/mamas.o diffusion3/lib/nr/nr.o diffusion3/lib/dr.o diffusion3/filters/diffusion/one_phase_pull.o diffusion3/filters/diffusion/two_phase_pull.o diffusion3/lib/diffapp.o diffusion3/ns/diffagent.o diffusion3/ns/diffrtg.o diffusion3/ns/difftimer.o diffusion3/filter_core/filter_core.o diffusion3/filter_core/iolog.o diffusion3/filter_core/iostats.o diffusion3/lib/main/attrs.o diffusion3/lib/main/events.o diffusion3/lib/main/iodev.o diffusion3/lib/main/iohook.o diffusion3/lib/main/timers.o diffusion3/lib/main/message.o diffusion3/lib/main/tools.o diffusion3/apps/gear_examples/gear_common.o diffusion3/apps/gear_examples/gear_receiver.o diffusion3/apps/gear_examples/gear_sender.o diffusion3/apps/rmst_examples/rmst_sink.o diffusion3/apps/rmst_examples/rmst_source.o diffusion3/apps/ping/1pp_ping_sender.o diffusion3/apps/ping/1pp_ping_receiver.o diffusion3/apps/ping/2pp_ping_sender.o diffusion3/apps/ping/2pp_ping_receiver.o diffusion3/apps/ping/ping_common.o diffusion3/apps/ping/push_receiver.o diffusion3/apps/ping/push_sender.o diffusion3/filters/gear/gear_attr.o diffusion3/filters/gear/gear.o diffusion3/filters/gear/gear_tools.o diffusion3/filters/misc/log.o diffusion3/filters/misc/srcrt.o diffusion3/filters/misc/tag.o diffusion3/filters/rmst/rmst.o diffusion3/filters/rmst/rmst_filter.o delaybox/delaybox.o packmime/packmime_HTTP.o packmime/packmime_HTTP_rng.o packmime/packmime_OL.o packmime/packmime_OL_ranvar.o packmime/packmime_ranvar.o gen/version.o gen/ns_tcl.o gen/ptypes.o  common/win32.o -L/usr/local/lib -ltclcl -L/usr/local/lib -lotcl -L/usr/local/lib -ltk8.4 -L/usr/local/lib -ltcl8.4 -lXext -lX11 -lnsl 
-ldl -lm -lm  **-lrt** -I./maser
maser/mamas.o: In function `mamasReasoner::mamasReasoner()':
mamas.cc:(.text+0x95): undefined reference to `NeoEnvironment::initFromNs(std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, int)'
maser/mamas.o: In function `mamasReasoner::build_ontology_tree(knBase&)':
mamas.cc:(.text+0x1c84): undefined reference to `NeoEnvironment::evaluateCommand(String const&)'
maser/mamas.o: In function `NeoEnvironment::readXmlFromMemory(char const*, char const*)':
mamas.cc:(.text._ZN14NeoEnvironment17readXmlFromMemoryEPKcS1_[NeoEnvironment::readXmlFromMemory(char const*, char const*)]+0x14): undefined reference to `Parser::readXmlFromMemory(char const*, char const*)'
collect2: ld returned 1 exit status
make: *** [ns] Error 1
```

these functions are defined and also the header files are included.

i am sorry for asking such basic questions as i am a beginner i C/C++ and i have encountered to work on a large project like NS2 the code of my project is also avaialable online if you want to look at the files mentioned in errors. [neoclassic]("https://code.google.com/p/ns2-neoclassic/source/browse/#svn%2Ftrunk%2Fcodice%2Fmaser")

> **dwhitney67 said:**
> It is critical that you learn to read if you want to advance in your studies.  Hmmm, perhaps I was not clear before...

The libraries need to be specified *after *your object files, not before.

For example, this statement is wrong:
```

g++ -lrt MyModule.o -o myprog

```
This one is correct:
```

g++ MyModule.o -lrt -o myprog

```
Note the ordering of the object file versus the library specification.

If you remove the library specifications from LDFLAGS and place them with LIB, then your build issues should be resolved.

---

### Post by dwhitney67 on 2012-06-19
](*,)

Have you considered defining these two libraries at the end of your g++ statement?
```

-lneoclassic -lxml2

```

In summary, I would be thrilled if you would post the errors of building your project with a command that looks like this:
```

g++ -o ns \
		common/tclAppInit.o  tools/random.o tools/rng.o tools/ranvar.o common/misc.o common/timer-handler.o common/scheduler.o common/object.o common/packet.o common/ip.o routing/route.o common/connector.o common/ttl.o trace/trace.o trace/trace-ip.o classifier/classifier.o classifier/classifier-addr.o classifier/classifier-hash.o classifier/classifier-virtual.o classifier/classifier-mcast.o classifier/classifier-bst.o classifier/classifier-mpath.o mcast/replicator.o classifier/classifier-mac.o classifier/classifier-qs.o classifier/classifier-port.o src_rtg/classifier-sr.o src_rtg/sragent.o src_rtg/hdr_src.o adc/ump.o qs/qsagent.o qs/hdr_qs.o apps/app.o apps/telnet.o tcp/tcplib-telnet.o tools/trafgen.o trace/traffictrace.o tools/pareto.o tools/expoo.o tools/cbr_traffic.o adc/tbf.o adc/resv.o adc/sa.o tcp/saack.o tools/measuremod.o adc/estimator.o adc/adc.o adc/ms-adc.o adc/timewindow-est.o adc/acto-adc.o adc/pointsample-est.o adc/salink.o adc/actp-adc.o adc/hb-adc.o adc/expavg-est.o adc/param-adc.o adc/null-estimator.o adc/adaptive-receiver.o apps/vatrcvr.o adc/consrcvr.o common/agent.o common/message.o apps/udp.o common/session-rtp.o apps/rtp.o tcp/rtcp.o common/ivs.o common/messpass.o common/tp.o common/tpm.o apps/worm.o tcp/tcp.o tcp/tcp-sink.o tcp/tcp-reno.o tcp/tcp-newreno.o tcp/tcp-vegas.o tcp/tcp-rbp.o tcp/tcp-full.o tcp/rq.o baytcp/tcp-full-bay.o baytcp/ftpc.o baytcp/ftps.o tcp/scoreboard.o tcp/scoreboard-rq.o tcp/tcp-sack1.o tcp/tcp-fack.o tcp/tcp-asym.o tcp/tcp-asym-sink.o tcp/tcp-fs.o tcp/tcp-asym-fs.o tcp/tcp-int.o tcp/chost.o tcp/tcp-session.o tcp/nilist.o sctp/sctp.o apps/sctp_app1.o sctp/sctp-timestamp.o sctp/sctp-hbAfterRto.o sctp/sctp-multipleFastRtx.o sctp/sctp-mfrHbAfterRto.o sctp/sctp-mfrTimestamp.o sctp/sctp-cmt.o sctp/sctpDebug.o tools/integrator.o tools/queue-monitor.o tools/flowmon.o tools/loss-monitor.o queue/queue.o queue/drop-tail.o adc/simple-intserv-sched.o queue/red.o queue/semantic-packetqueue.o queue/semantic-red.o tcp/ack-recons.o queue/sfq.o queue/fq.o queue/drr.o queue/srr.o queue/cbq.o queue/jobs.o queue/marker.o queue/demarker.o link/hackloss.o queue/errmodel.o queue/fec.o link/delay.o tcp/snoop.o gaf/gaf.o link/dynalink.o routing/rtProtoDV.o common/net-interface.o mcast/ctrMcast.o mcast/mcast_ctrl.o mcast/srm.o common/sessionhelper.o queue/delaymodel.o mcast/srm-ssm.o mcast/srm-topo.o routing/alloc-address.o routing/address.o lib/int.Vec.o lib/int.RVec.o lib/dmalloc_support.o webcache/http.o webcache/tcp-simple.o webcache/pagepool.o webcache/inval-agent.o webcache/tcpapp.o webcache/http-aux.o webcache/mcache.o webcache/webtraf.o webcache/webserver.o webcache/logweb.o empweb/empweb.o empweb/empftp.o realaudio/realaudio.o mac/lanRouter.o classifier/filter.o common/pkt-counter.o common/Decapsulator.o common/Encapsulator.o common/encap.o mac/channel.o mac/mac.o mac/ll.o mac/mac-802_11.o mac/mac-802_3.o mac/mac-tdma.o mac/smac.o mobile/mip.o mobile/mip-reg.o mobile/gridkeeper.o mobile/propagation.o mobile/tworayground.o mobile/antenna.o mobile/omni-antenna.o mobile/shadowing.o mobile/shadowing-vis.o mobile/dumb-agent.o common/bi-connector.o common/node.o common/mobilenode.o mac/arp.o mobile/god.o mobile/dem.o mobile/topography.o mobile/modulation.o queue/priqueue.o queue/dsr-priqueue.o mac/phy.o mac/wired-phy.o mac/wireless-phy.o mac/mac-timers.o trace/cmu-trace.o mac/varp.o mac/mac-simple.o satellite/sat-hdlc.o dsdv/dsdv.o dsdv/rtable.o queue/rtqueue.o routing/rttable.o imep/imep.o imep/dest_queue.o imep/imep_api.o imep/imep_rt.o imep/rxmit_queue.o imep/imep_timers.o imep/imep_util.o imep/imep_io.o tora/tora.o tora/tora_api.o tora/tora_dest.o tora/tora_io.o tora/tora_logs.o tora/tora_neighbor.o dsr/dsragent.o dsr/hdr_sr.o dsr/mobicache.o dsr/path.o dsr/requesttable.o dsr/routecache.o dsr/add_sr.o dsr/dsr_proto.o dsr/flowstruct.o dsr/linkcache.o dsr/simplecache.o dsr/sr_forwarder.o aodv/aodv_logs.o aodv/aodv.o aodv/aodv_rtable.o aodv/aodv_rqueue.o common/ns-process.o satellite/satgeometry.o satellite/sathandoff.o satellite/satlink.o satellite/satnode.o satellite/satposition.o satellite/satroute.o satellite/sattrace.o rap/raplist.o rap/rap.o rap/media-app.o rap/utilities.o common/fsm.o tcp/tcp-abs.o diffusion/diffusion.o diffusion/diff_rate.o diffusion/diff_prob.o diffusion/diff_sink.o diffusion/flooding.o diffusion/omni_mcast.o diffusion/hash_table.o diffusion/routing_table.o diffusion/iflist.o tcp/tfrc.o tcp/tfrc-sink.o mobile/energy-model.o apps/ping.o tcp/tcp-rfc793edu.o queue/rio.o queue/semantic-rio.o tcp/tcp-sack-rh.o tcp/scoreboard-rh.o plm/loss-monitor-plm.o plm/cbr-traffic-PP.o linkstate/hdr-ls.o mpls/classifier-addr-mpls.o mpls/ldp.o mpls/mpls-module.o routing/rtmodule.o classifier/classifier-hier.o routing/addr-params.o nix/hdr_nv.o nix/classifier-nix.o nix/nixnode.o routealgo/rnode.o routealgo/bfs.o routealgo/rbitmap.o routealgo/rlookup.o routealgo/routealgo.o nix/nixvec.o nix/nixroute.o diffserv/dsred.o diffserv/dsredq.o diffserv/dsEdge.o diffserv/dsCore.o diffserv/dsPolicy.o diffserv/ew.o diffserv/dewp.o queue/red-pd.o queue/pi.o queue/vq.o queue/rem.o queue/gk.o pushback/rate-limit.o pushback/rate-limit-strategy.o pushback/ident-tree.o pushback/agg-spec.o pushback/logging-data-struct.o pushback/rate-estimator.o pushback/pushback-queue.o pushback/pushback.o common/parentnode.o trace/basetrace.o common/simulator.o asim/asim.o common/scheduler-map.o common/splay-scheduler.o linkstate/ls.o linkstate/rtProtoLS.o pgm/classifier-pgm.o pgm/pgm-agent.o pgm/pgm-sender.o pgm/pgm-receiver.o mcast/rcvbuf.o mcast/classifier-lms.o mcast/lms-agent.o mcast/lms-receiver.o mcast/lms-sender.o queue/delayer.o xcp/xcpq.o xcp/xcp.o xcp/xcp-end-sys.o wpan/p802_15_4csmaca.o wpan/p802_15_4fail.o wpan/p802_15_4hlist.o wpan/p802_15_4mac.o wpan/p802_15_4nam.o wpan/p802_15_4phy.o wpan/p802_15_4sscs.o wpan/p802_15_4timer.o wpan/p802_15_4trace.o wpan/p802_15_4transac.o maser/maser.o maser/mamas.o diffusion3/lib/nr/nr.o diffusion3/lib/dr.o diffusion3/filters/diffusion/one_phase_pull.o diffusion3/filters/diffusion/two_phase_pull.o diffusion3/lib/diffapp.o diffusion3/ns/diffagent.o diffusion3/ns/diffrtg.o diffusion3/ns/difftimer.o diffusion3/filter_core/filter_core.o diffusion3/filter_core/iolog.o diffusion3/filter_core/iostats.o diffusion3/lib/main/attrs.o diffusion3/lib/main/events.o diffusion3/lib/main/iodev.o diffusion3/lib/main/iohook.o diffusion3/lib/main/timers.o diffusion3/lib/main/message.o diffusion3/lib/main/tools.o diffusion3/apps/gear_examples/gear_common.o diffusion3/apps/gear_examples/gear_receiver.o diffusion3/apps/gear_examples/gear_sender.o diffusion3/apps/rmst_examples/rmst_sink.o diffusion3/apps/rmst_examples/rmst_source.o diffusion3/apps/ping/1pp_ping_sender.o diffusion3/apps/ping/1pp_ping_receiver.o diffusion3/apps/ping/2pp_ping_sender.o diffusion3/apps/ping/2pp_ping_receiver.o diffusion3/apps/ping/ping_common.o diffusion3/apps/ping/push_receiver.o diffusion3/apps/ping/push_sender.o diffusion3/filters/gear/gear_attr.o diffusion3/filters/gear/gear.o diffusion3/filters/gear/gear_tools.o diffusion3/filters/misc/log.o diffusion3/filters/misc/srcrt.o diffusion3/filters/misc/tag.o diffusion3/filters/rmst/rmst.o diffusion3/filters/rmst/rmst_filter.o delaybox/delaybox.o packmime/packmime_HTTP.o packmime/packmime_HTTP_rng.o packmime/packmime_OL.o packmime/packmime_OL_ranvar.o packmime/packmime_ranvar.o gen/version.o gen/ns_tcl.o gen/ptypes.o  common/win32.o -L/usr/local/lib -ltclcl -L/usr/local/lib -lotcl -L/usr/local/lib -ltk8.4 -L/usr/local/lib -ltcl8.4 -lXext -lX11 -lnsl 
-ldl -lm -lm  -lrt **-lneoclassic -lxml2**

```

P.S.  You do not require any -I options when linking; I removed the following from the statement above:
```

-I./maser

```

---

### Post by hasanalikhattak on 2012-06-19
sorry, for the typo. :icon_frown:
actually i had done that but i had a mistake while posting here.
the error is still there. :confused:
```
g++  -o ns \
		common/tclAppInit.o  tools/random.o tools/rng.o tools/ranvar.o common/misc.o common/timer-handler.o common/scheduler.o common/object.o common/packet.o common/ip.o routing/route.o common/connector.o common/ttl.o trace/trace.o trace/trace-ip.o classifier/classifier.o classifier/classifier-addr.o classifier/classifier-hash.o classifier/classifier-virtual.o classifier/classifier-mcast.o classifier/classifier-bst.o classifier/classifier-mpath.o mcast/replicator.o classifier/classifier-mac.o classifier/classifier-qs.o classifier/classifier-port.o src_rtg/classifier-sr.o src_rtg/sragent.o src_rtg/hdr_src.o adc/ump.o qs/qsagent.o qs/hdr_qs.o apps/app.o apps/telnet.o tcp/tcplib-telnet.o tools/trafgen.o trace/traffictrace.o tools/pareto.o tools/expoo.o tools/cbr_traffic.o adc/tbf.o adc/resv.o adc/sa.o tcp/saack.o tools/measuremod.o adc/estimator.o adc/adc.o adc/ms-adc.o adc/timewindow-est.o adc/acto-adc.o adc/pointsample-est.o adc/salink.o adc/actp-adc.o adc/hb-adc.o adc/expavg-est.o adc/param-adc.o adc/null-estimator.o adc/adaptive-receiver.o apps/vatrcvr.o adc/consrcvr.o common/agent.o common/message.o apps/udp.o common/session-rtp.o apps/rtp.o tcp/rtcp.o common/ivs.o common/messpass.o common/tp.o common/tpm.o apps/worm.o tcp/tcp.o tcp/tcp-sink.o tcp/tcp-reno.o tcp/tcp-newreno.o tcp/tcp-vegas.o tcp/tcp-rbp.o tcp/tcp-full.o tcp/rq.o baytcp/tcp-full-bay.o baytcp/ftpc.o baytcp/ftps.o tcp/scoreboard.o tcp/scoreboard-rq.o tcp/tcp-sack1.o tcp/tcp-fack.o tcp/tcp-asym.o tcp/tcp-asym-sink.o tcp/tcp-fs.o tcp/tcp-asym-fs.o tcp/tcp-int.o tcp/chost.o tcp/tcp-session.o tcp/nilist.o sctp/sctp.o apps/sctp_app1.o sctp/sctp-timestamp.o sctp/sctp-hbAfterRto.o sctp/sctp-multipleFastRtx.o sctp/sctp-mfrHbAfterRto.o sctp/sctp-mfrTimestamp.o sctp/sctp-cmt.o sctp/sctpDebug.o tools/integrator.o tools/queue-monitor.o tools/flowmon.o tools/loss-monitor.o queue/queue.o queue/drop-tail.o adc/simple-intserv-sched.o queue/red.o queue/semantic-packetqueue.o queue/semantic-red.o tcp/ack-recons.o queue/sfq.o queue/fq.o queue/drr.o queue/srr.o queue/cbq.o queue/jobs.o queue/marker.o queue/demarker.o link/hackloss.o queue/errmodel.o queue/fec.o link/delay.o tcp/snoop.o gaf/gaf.o link/dynalink.o routing/rtProtoDV.o common/net-interface.o mcast/ctrMcast.o mcast/mcast_ctrl.o mcast/srm.o common/sessionhelper.o queue/delaymodel.o mcast/srm-ssm.o mcast/srm-topo.o routing/alloc-address.o routing/address.o lib/int.Vec.o lib/int.RVec.o lib/dmalloc_support.o webcache/http.o webcache/tcp-simple.o webcache/pagepool.o webcache/inval-agent.o webcache/tcpapp.o webcache/http-aux.o webcache/mcache.o webcache/webtraf.o webcache/webserver.o webcache/logweb.o empweb/empweb.o empweb/empftp.o realaudio/realaudio.o mac/lanRouter.o classifier/filter.o common/pkt-counter.o common/Decapsulator.o common/Encapsulator.o common/encap.o mac/channel.o mac/mac.o mac/ll.o mac/mac-802_11.o mac/mac-802_3.o mac/mac-tdma.o mac/smac.o mobile/mip.o mobile/mip-reg.o mobile/gridkeeper.o mobile/propagation.o mobile/tworayground.o mobile/antenna.o mobile/omni-antenna.o mobile/shadowing.o mobile/shadowing-vis.o mobile/dumb-agent.o common/bi-connector.o common/node.o common/mobilenode.o mac/arp.o mobile/god.o mobile/dem.o mobile/topography.o mobile/modulation.o queue/priqueue.o queue/dsr-priqueue.o mac/phy.o mac/wired-phy.o mac/wireless-phy.o mac/mac-timers.o trace/cmu-trace.o mac/varp.o mac/mac-simple.o satellite/sat-hdlc.o dsdv/dsdv.o dsdv/rtable.o queue/rtqueue.o routing/rttable.o imep/imep.o imep/dest_queue.o imep/imep_api.o imep/imep_rt.o imep/rxmit_queue.o imep/imep_timers.o imep/imep_util.o imep/imep_io.o tora/tora.o tora/tora_api.o tora/tora_dest.o tora/tora_io.o tora/tora_logs.o tora/tora_neighbor.o dsr/dsragent.o dsr/hdr_sr.o dsr/mobicache.o dsr/path.o dsr/requesttable.o dsr/routecache.o dsr/add_sr.o dsr/dsr_proto.o dsr/flowstruct.o dsr/linkcache.o dsr/simplecache.o dsr/sr_forwarder.o aodv/aodv_logs.o aodv/aodv.o aodv/aodv_rtable.o aodv/aodv_rqueue.o common/ns-process.o satellite/satgeometry.o satellite/sathandoff.o satellite/satlink.o satellite/satnode.o satellite/satposition.o satellite/satroute.o satellite/sattrace.o rap/raplist.o rap/rap.o rap/media-app.o rap/utilities.o common/fsm.o tcp/tcp-abs.o diffusion/diffusion.o diffusion/diff_rate.o diffusion/diff_prob.o diffusion/diff_sink.o diffusion/flooding.o diffusion/omni_mcast.o diffusion/hash_table.o diffusion/routing_table.o diffusion/iflist.o tcp/tfrc.o tcp/tfrc-sink.o mobile/energy-model.o apps/ping.o tcp/tcp-rfc793edu.o queue/rio.o queue/semantic-rio.o tcp/tcp-sack-rh.o tcp/scoreboard-rh.o plm/loss-monitor-plm.o plm/cbr-traffic-PP.o linkstate/hdr-ls.o mpls/classifier-addr-mpls.o mpls/ldp.o mpls/mpls-module.o routing/rtmodule.o classifier/classifier-hier.o routing/addr-params.o nix/hdr_nv.o nix/classifier-nix.o nix/nixnode.o routealgo/rnode.o routealgo/bfs.o routealgo/rbitmap.o routealgo/rlookup.o routealgo/routealgo.o nix/nixvec.o nix/nixroute.o diffserv/dsred.o diffserv/dsredq.o diffserv/dsEdge.o diffserv/dsCore.o diffserv/dsPolicy.o diffserv/ew.o diffserv/dewp.o queue/red-pd.o queue/pi.o queue/vq.o queue/rem.o queue/gk.o pushback/rate-limit.o pushback/rate-limit-strategy.o pushback/ident-tree.o pushback/agg-spec.o pushback/logging-data-struct.o pushback/rate-estimator.o pushback/pushback-queue.o pushback/pushback.o common/parentnode.o trace/basetrace.o common/simulator.o asim/asim.o common/scheduler-map.o common/splay-scheduler.o linkstate/ls.o linkstate/rtProtoLS.o pgm/classifier-pgm.o pgm/pgm-agent.o pgm/pgm-sender.o pgm/pgm-receiver.o mcast/rcvbuf.o mcast/classifier-lms.o mcast/lms-agent.o mcast/lms-receiver.o mcast/lms-sender.o queue/delayer.o xcp/xcpq.o xcp/xcp.o xcp/xcp-end-sys.o wpan/p802_15_4csmaca.o wpan/p802_15_4fail.o wpan/p802_15_4hlist.o wpan/p802_15_4mac.o wpan/p802_15_4nam.o wpan/p802_15_4phy.o wpan/p802_15_4sscs.o wpan/p802_15_4timer.o wpan/p802_15_4trace.o wpan/p802_15_4transac.o maser/maser.o maser/mamas.o diffusion3/lib/nr/nr.o diffusion3/lib/dr.o diffusion3/filters/diffusion/one_phase_pull.o diffusion3/filters/diffusion/two_phase_pull.o diffusion3/lib/diffapp.o diffusion3/ns/diffagent.o diffusion3/ns/diffrtg.o diffusion3/ns/difftimer.o diffusion3/filter_core/filter_core.o diffusion3/filter_core/iolog.o diffusion3/filter_core/iostats.o diffusion3/lib/main/attrs.o diffusion3/lib/main/events.o diffusion3/lib/main/iodev.o diffusion3/lib/main/iohook.o diffusion3/lib/main/timers.o diffusion3/lib/main/message.o diffusion3/lib/main/tools.o diffusion3/apps/gear_examples/gear_common.o diffusion3/apps/gear_examples/gear_receiver.o diffusion3/apps/gear_examples/gear_sender.o diffusion3/apps/rmst_examples/rmst_sink.o diffusion3/apps/rmst_examples/rmst_source.o diffusion3/apps/ping/1pp_ping_sender.o diffusion3/apps/ping/1pp_ping_receiver.o diffusion3/apps/ping/2pp_ping_sender.o diffusion3/apps/ping/2pp_ping_receiver.o diffusion3/apps/ping/ping_common.o diffusion3/apps/ping/push_receiver.o diffusion3/apps/ping/push_sender.o diffusion3/filters/gear/gear_attr.o diffusion3/filters/gear/gear.o diffusion3/filters/gear/gear_tools.o diffusion3/filters/misc/log.o diffusion3/filters/misc/srcrt.o diffusion3/filters/misc/tag.o diffusion3/filters/rmst/rmst.o diffusion3/filters/rmst/rmst_filter.o delaybox/delaybox.o packmime/packmime_HTTP.o packmime/packmime_HTTP_rng.o packmime/packmime_OL.o packmime/packmime_OL_ranvar.o packmime/packmime_ranvar.o gen/version.o gen/ns_tcl.o gen/ptypes.o  common/win32.o -L/usr/local/lib -ltclcl -L/usr/local/lib -lotcl -L/usr/local/lib -ltk8.4 -L/usr/local/lib -ltcl8.4 -lXext -lX11 -lnsl -ldl -lm -lm 
**-lrt -lneoclassic -lxml2**
maser/mamas.o: In function `mamasReasoner::mamasReasoner()':
mamas.cc:(.text+0x95): undefined reference to `NeoEnvironment::initFromNs(std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, std::basic_ostringstream<char, std::char_traits<char>, std::allocator<char> >&, int)'
maser/mamas.o: In function `mamasReasoner::build_ontology_tree(knBase&)':
mamas.cc:(.text+0x1c84): undefined reference to `NeoEnvironment::evaluateCommand(String const&)'
maser/mamas.o: In function `NeoEnvironment::readXmlFromMemory(char const*, char const*)':
mamas.cc:(.text._ZN14NeoEnvironment17readXmlFromMemoryEPKcS1_[NeoEnvironment::readXmlFromMemory(char const*, char const*)]+0x14): undefined reference to `Parser::readXmlFromMemory(char const*, char const*)'
collect2: ld returned 1 exit status
make: *** [ns] Error 1
```

---

