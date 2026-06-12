---
title: "c++ stl map"
date: 2015-05-19
forum: Programming Talk
---

### Post by pdk2 on 2015-05-19
Hello
I have the following map :

        listOfPolicyRuleInfo CPCRF::m_mlistOfCliConfiguredPolicyRules;

where typedef map<string, PolicyRuleInfo> listOfPolicyRuleInfo;

    where PolicyRuleInfo is a struct 

    struct PolicyRuleInfo{
        BearerQoSInfo stBearerQoS;
        TFTInfo stTFTInfo;
        PolicyRuleInfo(){};
        PolicyRuleInfo( BearerQoSInfo const& qos, TFTInfo const& tft)
           : stBearerQoS(qos), stTFTInfo(tft)
        { }
    };
    listOfPolicyRuleInfo m_mlistOfCliConfiguredPolicyRules = 
    boost::assign::map_list_of("PolicyRule_Fred", PolicyRuleInfo( BearerQoSInfo(9), TFTInfo()))
                               ("PolicyRule_Voice_C", PolicyRuleInfo( BearerQoSInfo(5), TFTInfo()))
                                ("PolicyRule_Voice_U", PolicyRuleInfo( BearerQoSInfo(1), TFTInfo()));

Above are the data strutures. Now within the code somewhere ,

        listOfPolicyRuleInfo::iterator it = m_mlistOfCliConfiguredPolicyRules.find("PolicyRule_Fred");

I get error when i try to print the contents of it.

on gdb i see the list

    (gdb)p m_mlistOfCliConfiguredPolicyRules
      ["PolicyRule_Fred"] = {stBearerQoS = {nQCI = 9, nMaxUlBitRate = 0, nMaxDlBitRate = 0,
          nGuarUlBitRate = 0, nGuarDlBitRate = 0, nPriorityLevel = 15,
          bPreEmptionCapabilityEnabled = false, bPreEmptionVulnerabilityEnabled = true,
          bQoSModified = false}, stTFTInfo = {static IPV4CompLen = 9 '\t',
          static PiNhCompLen = 2 '\002', static SinglePortCompLen = 3 '\003',
          static PortRangeCompLen = 5 '\005', static TypeOfServiceCompLen = 3 '\003',
          static FilterHdrLen = 3 '\003', nTFTLen = 0, eOpCode = 3653872, bEBit = false,
          nNumPktFilters = 0 '\000', mFilterId2TFTFilters = std::map with 0 elements,
          vTFTParams = std::vector of length 0, capacity 0}},

      ["PolicyRule_Voice_C"] = {stBearerQoS = {nQCI = 5, nMaxUlBitRate = 0, nMaxDlBitRate = 0,
          nGuarUlBitRate = 0, nGuarDlBitRate = 0, nPriorityLevel = 15,
          bPreEmptionCapabilityEnabled = false, bPreEmptionVulnerabilityEnabled = true,
          bQoSModified = false}, stTFTInfo = {static IPV4CompLen = 9 '\t',
          static PiNhCompLen = 2 '\002', static SinglePortCompLen = 3 '\003',
          static PortRangeCompLen = 5 '\005', static TypeOfServiceCompLen = 3 '\003',
          static FilterHdrLen = 3 '\003', nTFTLen = 0, eOpCode = 3943806, bEBit = false,
          nNumPktFilters = 0 '\000', mFilterId2TFTFilters = std::map with 0 elements,
          vTFTParams = std::vector of length 0, capacity 0}},

      ["PolicyRule_Voice_U"] = {stBearerQoS = {nQCI = 1, nMaxUlBitRate = 0, nMaxDlBitRate = 0,
          nGuarUlBitRate = 0, nGuarDlBitRate = 0, nPriorityLevel = 15,
          bPreEmptionCapabilityEnabled = false, bPreEmptionVulnerabilityEnabled = true,
          bQoSModified = false}, stTFTInfo = {static IPV4CompLen = 9 '\t',
          static PiNhCompLen = 2 '\002', static SinglePortCompLen = 3 '\003',
          static PortRangeCompLen = 5 '\005', static TypeOfServiceCompLen = 3 '\003',
          static FilterHdrLen = 3 '\003', nTFTLen = 0, eOpCode = 4870778, bEBit = false,
          nNumPktFilters = 0 '\000', mFilterId2TFTFilters = std::map with 0 elements,
          vTFTParams = std::vector of length 0, capacity 0}}
    But
    (gdb) p it
    $6 = {first = Traceback (most recent call last):
      File "/usr/lib/../share/gdb/python/libstdcxx/v6/printers.py", line 558, in to_string
        return self.val['_M_dataplus']['_M_p'].lazy_string (length = len)
    RuntimeError: Cannot access memory at address 0xfffffff4
    , second = {stBearerQoS = {nQCI = 0, nMaxUlBitRate = 0, nMaxDlBitRate = 0,
          nGuarUlBitRate = 172411760, nGuarDlBitRate = 172411760, nPriorityLevel = 0,
          bPreEmptionCapabilityEnabled = false, bPreEmptionVulnerabilityEnabled = false,
          bQoSModified = false}, stTFTInfo = {static IPV4CompLen = 9 '\t',
          static PiNhCompLen = 2 '\002', static SinglePortCompLen = 3 '\003',
          static PortRangeCompLen = 5 '\005', static TypeOfServiceCompLen = 3 '\003',
          static FilterHdrLen = 3 '\003', nTFTLen = 0, eOpCode = 174849016, bEBit = 128,
          nNumPktFilters = 251 '\373', mFilterId2TFTFilters = std::map with 0 elements,
          vTFTParams = std::vector of length 0, capacity 0}}}

Could some c++ stl experts help me with this issue please ?

thanks,
~pdk

---

