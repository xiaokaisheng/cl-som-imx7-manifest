# Compulab IMX7模块的repo manifest
## 简介
  * [Compulab IMX7的BSP](https://github.com/compulab-yokneam/meta-bsp-imx7.git)关于生成Full command line core image的步骤
    ```
    repo init -u git://source.codeaurora.org/external/imx/imx-manifest.git -b imx-linux-sumo -m imx-4.14.98-2.0.0_ga.xml
    repo sync
    git clone -b master https://github.com/compulab-yokneam/meta-bsp-imx7.git sources/meta-bsp-imx7/
    MACHINE=cl-som-imx7 DISTRO=fsl-imx-fb source sources/meta-bsp-imx7/tools/setup-env -b build-fb-imx7
    bitbake -k core-image-full-cmdline
    ```
  * 使用repo manifest default.xml自动实现
    * 包含imx-4.14.98-2.0.0_ga.xml, 该文件的来源
      ```
      git clone git://source.codeaurora.org/external/imx/imx-manifest.git
      cd imx-manifest
      git checkout imx-linux-sumo
      ```
      从目录下复制文件: imx-4.14.98-2.0.0_ga.xml
    * 包含compulab的meta-bsp-imx7
      ```
      git repo: https://github.com/compulab-yokneam/meta-bsp-imx7.git
      ```
    * 包含meta-compulab-imx7-tutorial, 定制化的recipes

## 使用default.xml生成镜像
  * 建立工作目录
    ```
    mkdir <repo-directory>
    cd <repo-directory>
    repo init -u <本目录内容的git repository>
    repo sync
    ```
  * 生成Full command line core image
    ```
    MACHINE=cl-som-imx7 DISTRO=fsl-imx-fb \
      source sources/meta-bsp-imx7/tools/setup-env -b build-fb-imx7
    bitbake -k core-image-full-cmdline
    ```
  * 在新建终端中继续生成
    ```
    cd <repo-directory>
    source setup-environment build-fb-imx7
    ```

