# 说明

- [ ] 添加脚本批量替换配置


### ubuntu源访问不了的问题
或许是因为通过代理访问ubuntu源比较慢的原因，导致ubuntu容器一律使用不了`apt update`
在directlist加入`archive.ubuntu.com`和`security.ubuntu.com`解决了问题

### 配置内网IP直连
#### 1. 配置direct模式
```
###### file: config.yaml ######
  - type: list
    file: ~/.SpechtLite/directlist
    adapter: direct

###### file: ~/.SpechtLite/directlist ######
# A类地址
10\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])
# B类地址
172\.(1[6789]|2[0-9]|3[01])\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])
# C类地址
192\.168\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])\.(1\d{2}|2[0-4]\d|25[0-5]|[1-9]\d|[0-9])
```

#### 2. 其实配置`country: --`也可以实现本地地址的直连
```
  # 当无法找到对应IP的地理位置信息时会返回“--”，这通常意味着这是一个内网IP。
  - type: country
    country: --
    match: true
    adapter: direct
```

