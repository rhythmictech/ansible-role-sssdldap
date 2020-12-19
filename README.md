# ansible-role-sssdldap

## Overview

This is a very opinionated role to configure `sssd` for LDAP authentication against OpenLDAP or Active Directory on RedHat-based systems, including Amazon Linux 2.

This role will install and configure `sssd` to support a single domain with basic LDAP authentication over TLS. It configures PAM to use `sssd` for all compatible services,
and configure OpenSSH server to source SSH public keys from LDAP via `sssd`. It bakes in CIS Level 1 compliance for the systems it touches.

## Usage

At a minimum, you must define the following vars:

* `sssdldap_ldap_uri`
* `sssdldap_bind_dn`
* `sssdldap_bind_pw`
* `sssdldap_search_base`

Their usage is documented in the defaults file.

If using TLS, you must ensure your system already trusts the LDAP TLS certificate in-use. The easiest way to do this is via the system-wide trust store; alternatively
you can point `sssd` at a different trusted certificate file with the var `sssdldap_cacert`.