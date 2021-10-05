# fail2ban

```
phil@phil-HP-ProBook-4740s:~$ sudo fail2ban-client status sshd
Status for the jail: sshd
|- Filter
|  |- Currently failed:	0
|  |- Total failed:	0
|  `- File list:	/var/log/auth.log
`- Actions
   |- Currently banned:	0
   |- Total banned:	1
   `- Banned IP list:	
phil@phil-HP-ProBook-4740s:~$ sudo telegraf -config telegraf2.conf 
2021-10-05T14:52:42Z I! Starting Telegraf 1.17.0
2021-10-05T14:52:42Z I! Loaded inputs: fail2ban
2021-10-05T14:52:42Z I! Loaded aggregators: 
2021-10-05T14:52:42Z I! Loaded processors: 
2021-10-05T14:52:42Z I! Loaded outputs: influxdb_v2
2021-10-05T14:52:42Z I! Tags enabled: host=phil-HP-ProBook-4740s
2021-10-05T14:52:42Z I! [agent] Config: Interval:10s, Quiet:false, Hostname:"phil-HP-ProBook-4740s", Flush Interval:10s

```
telegraf.conf
```
[[outputs.influxdb_v2]]
  ## The URLs of the InfluxDB cluster nodes.
  ##
  ## Multiple URLs can be specified for a single cluster, only ONE of the
  ## urls will be written to each interval.
  ## urls exp: http://127.0.0.1:8086
  urls = ["http://192.168.15.15:8086"]

  ## Token for authentication.
  ##token = "$INFLUX_TOKEN"
  ##token = "CBBjXqncS769HbV_646yJUDwlhdBjDK5wDsAhCwNB4T9BEfNZ5Il0ZVRpqBSFBZsJT>
  token = "ZXtuHY3CVzc6qE_ZkiN36q7ie1mD3CXFetQHvm8eCs3juHKnmW12OniQre90rd_kO5ws>
  ## Organization is the name of the organization you wish to write to; must ex>
  organization = "test-org"

  ## Destination bucket to write into.
  bucket = "fail2ban"

[[inputs.fail2ban]]
```

