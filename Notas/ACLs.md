# ACLs

> Se ponen lo más cerca al destino ...

Control básico de seguridad que a partir de parámetros de red como dirección IP ...

- Comandos
  
  - `deny` ...
  
  - `permit` ...

---

# Tipos

- **ACLs estándar**: Permiten o deniegan tráfico con base en la IP origen del paquete
  
  ```shell
  acces-list 10 permit 188.98.0.0 0.0.255.255
  ```

- **ACLs extendidad**: Permiten o deniegan tráfico con base en
  
  - Protocolo
  
  - Dirección IP Origen
  
  - Dirección IP Destino
  
  ```shell
  # Permita solo tráfico HTTP
  access-list 104 permit tcp any host 201.33.44.55 eq 80
  ```

---



## ACLs con nombre

```shell
# Standard
ip access-list standard [nombre_de_la_acl]
# Extended
ip access-list extended [nombre_de_la_acl]
```

```shell
# Permitir cualquier IP
R1(config-ext-nacl)# 50 permit ip any any
# Eliminar línea anterior
R1(config-ext-nacl)# no 50
```

---

### Para configurar ACLs en simulacion "RED EJEMPLO.pkt"

> Intento erróneo

- `int vlan 30 in`

- `permit ip 204.33.11.0 0.0.0.63 any`

- `ip access-list ext wifi`

- `100 permit`

- `int vlan 30`

- `ip access wifi in`

---

- `vlan 10 204.33.11.64/26`

- `vlan 10 204.33.11.128/27`

- `vlan 10 204.33.11.160/27`

- `vlan 10 204.33.11.192/28`

- `vlan 10 204.33.11.0/26`

---

- `20 permit udp 204.33.11.0 0.0.0.63 host 204.33.11.194 eq 53`

- `50 deny ip 204.33.11.0 0.0.0.63 204.33.11.0`

- `50 deny ip 204.33.11.0 0.0.0.63 0.0.0.265`

- `15 permit udp any host 204.33.11.194 eq 67`

---

#### 2) Desde redes externas permitir acceso únicamente

- `permit tcp any host 204.33.11.194 eq 80`

- `permit tcp any host 204.33.11.194 eq 443`

- `permit udp any host 204.33.11.194 eq 53`

- `300 permit icmp any 204.33.11.0 0.0.0.255 unreachable`

- `350 permit icmp any 204.33.11.160 0.0.0.31 echo`

- `500 deny ip any any`

- `400 permit tcp any 204.33.11.0 0.0.0.255 established`

- `permit udp any eq 53 204.33.11.0 0.0.0.255`

> `serial 0/1/0 in`

#### 3) Solo desde sistemas se permiten pruebas ping a cualquier destino

- ``


