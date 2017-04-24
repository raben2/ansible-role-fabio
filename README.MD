Ansible Role Fabio
==================

This role installs fabio 0conf loadbalancer with some rudimentary configuration 

### Features
 - HTTP Loadbalancing
 - HTTPS Loadbalancing
 - ClientCert Authentication
 - TLS+SNI 

### ToDo
 - implement other certificate stores than file
 - extend configuration templates

### Requirements

[Ansible role golang](https://github.com/raben2/ansible-golang)

### Usage
Refer to the defaults file for configuration parameters

#### TLS
put your crt and key (e.g example.com) in the files directory and set the following hostvars: 
```
fabio_install_certificates: True
fabio_certificates:
  - example.com
```

### SNI
since your internal dns would probably not resolve your domain name the sni configuration will create a host entry on the lb server
```
fabio_sni: True
fabio_sni_backends:
    - domain: example.com
      ip: 127.0.0.1
```

### Client certificates
File based certificate stores are supported and can be configured as follows:
```
fabio_install_client_certificates: True
fabio_client_cert_store: client #name of the certstore
fabio_client_certificates:
  - example.com
```

License
-------

LGPL

Author Information
------------------

- Georg Rabenstein raben2
