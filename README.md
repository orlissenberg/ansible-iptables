Role Name
=========

Ansible iptables role for Debian 7/8

Requirements
------------

No pre-requisites required.

Role Variables
--------------

...

Dependencies
------------

None

Example Playbook
----------------

...

License
-------

MIT

Notes
-----

Check if the script works:

    sudo ifup --all -v

    # show the filter table
    sudo iptables --list -v

[Docker Network Configuration](https://docs.docker.com/v1.5/articles/networking/#communication-between-containers)

    # show the nat table
    sudo iptables -t nat --list

    # according to the docs
    Chain POSTROUTING (policy ACCEPT)
    target      prot  opt  source         destination
    MASQUERADE  all   --   172.17.0.0/16  !172.17.0.0/16

    # set iptables masquerade
    sudo iptables -t nat -A POSTROUTING -j MASQUERADE  ! -d 172.17.0.0/16 -s 172.17.0.0/16 -p all

    # testing
    docker run busybox ping -c 1 192.203.230.10

    # restart fail2ban
    sudo systemctl restart fail2ban

[How to Disable/Enable IP forwarding in Linux](https://linuxconfig.org/how-to-turn-on-off-ip-forwarding-in-linux)
