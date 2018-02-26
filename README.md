# spectre-meltdown-checkHow to use this playbook to check "spectre & meltdown" vulnerabilities

1. Install Ansible

# subscription-manager repos --enable rhel-7-server-extras-rpms
# yum install ansible

Reference: https://access.redhat.com/articles/3174981


2. Create ssh key-pairs for all the hosts you want to check

# ssh-keygen
# ssh-copy -i /root/.ssh/id_rsa.pub root@<the-host-you-need-to-check>


3. Edit "hosts" files

Record all the hostname/IP you wan to check.


4. Execute playbook

ansible-playbook -i hosts spectre-meltdown.yml 

5. Check results

/root/microcodelog.txt:  All host hit Variant #2 (Spectre) and need to update CPU microcode
/root/patchlog.txt: All host hit Variant #1 (Spectre) or Variant #3 (Meltdown) and need to patch


