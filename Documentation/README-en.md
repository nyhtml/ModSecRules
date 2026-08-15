# ModSecRules
ModSecurity Tools Rules List

## Table of Contents
* 500001 — Trusted IP Bypass
* 500101 — File Probing
* 500201 — Server Fingerprinting
* 500301 — Hosting Panel Probing
* 500401 — WordPress Core Probing
* 500501 — WordPress Plugin Probing
* 500601 — CMS Reconnaissance
* 500701 — Malware Probing

```TEXT
# ============================
# 500101 — File Probing
# ============================
SecRule REQUEST_URI "@rx \.(shtml|env|bak|old|inc|config)$|/(\.git|\.svn)(/|$)" "id:500101,phase:1,deny,status:403,msg:'Bot trap: File Probe',tag:'Sipylus',tag:'bottrap',tag:'file-probe'"
```

```TEXT
# ============================
# 500201 — Server Fingerprinting
# ============================
SecRule REQUEST_URI "@rx ^/(server-status|phpinfo\.php|cgi-bin)(/|$)" "id:500201,phase:1,deny,status:403,msg:'Bot trap: Server Fingerprinting',tag:'Sipylus',tag:'bottrap',tag:'server-fingerprint'"
```

```TEXT
# ============================
# 500301 — Hosting Panel Probing
# ============================
SecRule REQUEST_URI "@rx ^/(whm|cpanel|webmail)(/|$)" "id:500301,phase:1,deny,status:403,msg:'Bot trap: Hosting Panel Probe (safe mode)',tag:'Sipylus',tag:'bottrap',tag:'hosting-panel'"
```

```TEXT
# ============================
# 500401 — WordPress Core Probing
# ============================
SecRule REQUEST_URI "@rx ^/(wp-login\.php|xmlrpc\.php|setup-config\.php|install\.php|admin\.php|plugins\.php|wp-includes/wlwmanifest\.xml)(\?|/|$)" "id:500401,phase:1,deny,status:403,msg:'Bot trap: WordPress Core Probe',tag:'Sipylus',tag:'bottrap',tag:'wordpress'"
```

```TEXT
# ============================
# 500501 — WordPress Plugin Probing
# ============================
SecRule REQUEST_URI "@rx ^/(admin\.php|aardvark\.php|license\.txt)(\?|/|$)" "id:500501,phase:1,deny,status:403,msg:'Bot trap: WordPress Core Probe',tag:'Sipylus',tag:'bottrap',tag:'wordpress'"
```

```TEXT
# ============================
# 500601 — CMS Reconnaissance
# ============================
SecRule REQUEST_URI "@rx ^/(vendor/|composer\.json$|package\.json$|\.env$|\.git(/|$))" "id:500601,phase:1,deny,status:403,msg:'Bot trap: CMS Reconnaissance',tag:'Sipylus',tag:'bottrap',tag:'cms-recon'"
```

```TEXT
# ============================
# 500701 — Malware Probing
# ============================
SecRule REQUEST_URI "@rx ^/(HNAP1|shell\.php|backdoor\.php|shell)(/|$)" "id:500701,phase:1,deny,status:403,msg:'Bot trap: Malware Probe',tag:'Sipylus',tag:'bottrap',tag:'malware-probe'"
```
