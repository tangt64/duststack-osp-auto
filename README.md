# 오픈스택 설치도구

## 프로젝트 설명

비 컨테이너 기반으로 오픈스택 설치를 지원해주는 도구 입니다.  지원하는 배포판은 다음과 같습니다.

- CentOS 7 and CentOS 8 Stream

- Debian and Ubuntu

- 아마도 기타 배포판도 지원 예정

- 

## 알림사항

- CentOS 7/8버전에서 제일 안정적으로 설치가 지원 됩니다.
- Debian/Ubuntu는 곧 지원할 예정입니다.

## 컴퓨터 사양

* **CPU:** Intel E5 or AMD Ryzen 7 3700X (Physical 8 core)
* **Memory:** Minimun 8 GiB
* **Disk:** least 500GiB HDD or SSD 1TiB Recommend
* **NIC:** least 1GiB 

이 플레이북은 가상머신이나 실제 물리머신에 설치가 가능 합니다.

## 가상머신에 설치하는 방법

### 가상머신 구성

가상머신을 생성하려면 다음과 같은 명령어로 실행 합니다.

```bash
# ansible-playbook -i inventory/classroom playbooks/classroom.yaml
```

위의 명령어를 실행하면 4대의 가상머신이 생성이 됩니다. 가상머신 갯수를 더 늘리고 싶으면 "duststack-ocp-auto/group_vars/classroom"에서 openstack파일에서 다음과 같이 내용을 변경 합니다.

```
openstack_nodes:
  - node1
  - node2
  - node3
  - node4
vdb_nodes:
  - node3
  - node4

storage_nodes:
  - node3
network_nodes:
```

서버는 최대 7대까지 kickstart파일이 구성이 되어 있습니다. 이 파일은 다음 위치에서 확인이 가능 합니다.

```
duststack-osp-auto/roles/virt-vms/files
node1.ks  node2.ks  node3.ks  node4.ks  node5.ks  node6.ks  node7.ks
```

자세한 내용은 위의 디렉터리에서 확인 부탁 드립니다.

If you wanna do build a Kubernetes Lab, Use this command.

```bash
# ansible-playbook -i inventory/classroom -e lab=kubernetes playbooks/classroom.yaml
# library/sshkeygensend.sh
```

## 문의

다른 문의사항이 있으시면 아래로 연락 주세요! :)

**E-Mail:** <bluehelix@gmail.com>
**Name:** 최국현(Choi Gook Hyun)

## License

GNU 2라이센스
