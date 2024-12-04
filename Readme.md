# 笔记转存脚本

本脚本用于部署部署腾讯云函数，上传markdown笔记到设定的对象存储中；

支持七牛云、S3协议、Webdav。

## 环境变量

部署时需要为该函数设置以下环境变量，如果不设置则需要在请求参数中携带：

- storage_type[可选]：值为“qiniu”或“s3”或“webdav”，默认s3；
- token[可选]：鉴权token，如果传入，则只有token输入正确的请求才会处理；

- qiniu_access_key[可选]：七牛云的access_key；
- qiniu_secret_key[可选]：七牛云的secret_key；
- bucket_domain[可选]：对象存储bucket的域名；

- bucket_name[可选]：对象存储bucket的名称；

- s3_endpoint[可选]：s3对象存储的域名；
- s3_region[可选]：s3对象存储的区域；
- s3_access_key[可选]：s3对象存储的密钥；
- s3_secret_key[可选]：s3对象存储的密钥；

- webdav_url[可选]：WebDav对象存储的域名；
- webdav_user[可选]：WebDav对象存储的用户名；
- webdav_psw[可选]：WebDav对象存储的密钥；

## 请求参数

该接口只接收POST请求，需要在请求体中传入如下参数：

> 注意：下面关于对象存储的鉴权参数为可选参数，如果不传入，则需要在创建云函数时，通过环境变量设定；

- token：用于鉴权；
- note_title：字符串类型；默认为随机字符串；
- note_content：字符串类型；笔记内容；

- note_url[可选]：网址链接，若传入该值，在忽略 `note_title` 和 `note_content`，改为获取网页内容；
- save_note_path[可选]：笔记保存路径；默认在根目录下创建 `000_cloud_note` 文件夹；
- note_source[可选]：笔记来源，用于标记笔记属性；默认为：`公众号【思维兵工厂】`；

- qiniu_access_key[可选]：七牛云的access_key；
- qiniu_secret_key[可选]：七牛云的secret_key；
- bucket_domain[可选]：对象存储bucket的域名；

- bucket_name[可选]：对象存储bucket的名称；

- s3_endpoint[可选]：s3对象存储的域名；
- s3_region[可选]：s3对象存储的区域；
- s3_access_key[可选]：s3对象存储的密钥；
- s3_secret_key[可选]：s3对象存储的密钥；

- webdav_url[可选]：WebDav对象存储的域名；
- webdav_user[可选]：WebDav对象存储的用户名；
- webdav_psw[可选]：WebDav对象存储的密钥；

## 容器部署

腾讯云函数的部署，经常遇到urllib包与requests包不兼容的情况，建议通过项目中的 DockerFile 文件构建容器镜像，基于容器部署云函数；





