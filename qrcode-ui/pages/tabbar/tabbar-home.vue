<template>
	<view class="content">
		<uni-section title="加解密相关" type="line" titleFontSize="18px">
			<uni-card @click="toHashEncrypt">
				<view class="eti">消息摘要算法支持:</view>
				<text class="uni-body">MD5、SHA、HMAC、PBKDF2</text>
			</uni-card>

			<uni-card @click="toSymmetryEncrypt">
				<view class="eti">对称加密算法支持:</view>
				<text class="uni-body">AES、DES、3DES(Triple DES)、RC4、Rabbit</text>
			</uni-card>

			<uni-card @click="toRsaEncrypt">
				<view class="eti">非对称加密算法支持:</view>
				<text class="uni-body">RSA</text>
			</uni-card>

			<uni-card @click="toBase64Encrypt">
				<view class="eti">其他常用的编码支持:</view>
				<text class="uni-body">Base64</text>
			</uni-card>

		</uni-section>

	</view>
</template>

<script>

	export default {
		data() {
			return {
				canClick: true,
				converList: ['进制相互转换', '数字转古代中文', '时间戳转日期', '日期时间计算器'],
				otherList: ['亲戚关系计算器', '二维码生成解析', '生肖查询', '节日头像合成', '氛围跑马灯']
			};
		},
		// onLoad：第一次创建页面执行
		onLoad() {},
		// onShow：每次进入页面都会执行
		onShow() {
			// this.testCrypto();
			// this.testRelation();
			// console.log(convertToCnMoney(1111131294.34));

			// let value = 24;
			// // 10 进制转16
			// console.log(baseTenToOther(value, 2));
			// console.log(baseTenToOther(value, 8));
			// console.log(baseTenToOther(value, 16));

			// console.log("特殊：",baseConversion('1000112312311134643643262461', 10, 36));
			// console.log(baseConversion(24, 10, 8));
			// console.log(baseConversion(24, 10, 16));

			// // 生肖
			// console.log(getZodiac(2023));

			// // 时间戳
			// console.log(getTimestampByDate());
			// console.log(getTimestampByDate(2023));
			// console.log(getTimestampByDate('2023-10-10'));
			// console.log(getTimestampByDate('2023-10-10 12:10:01'));
			// console.log(getTimestampByDate('2023-01-01 08:00:00'));
			// console.log(getDateByTimestamp(1666315175417));
			// console.log(getDateByTimestamp(1672531200000));
			// console.log(getDateByTimestamp(1696911001000));
			// console.log(getDateByTimestamp());
			// console.log(getDateAddOrSubDay(-3));
			// console.log(getDateAddOrSubDay(-25, '2022-10-21 12:10:10'));


		},
		//分享
		onShareAppMessage(res) {
			if (res.from === 'menu') { // 来自页面内分享按钮
				console.log(res.target)
			}
			return {
				title: '巨好用的有趣工具库',
				path: '/pages/tabbar/tabbar-home'
			}
		},
		methods: {
			encryptChange(e) {
				let {
					index
				} = e.detail;
				console.log('你点击了第几个：', index);
			},
			converChange(e) {
				let {
					index
				} = e.detail;
				console.log('你点击了第几个：', index);
			},
			otherChange(e) {
				let {
					index
				} = e.detail;
				console.log('你点击了第几个：', index);
			},
			toHashEncrypt() {
				this.toPage('/pages/tabbar/tools/hash-encrypt');
			},
			toSymmetryEncrypt() {
				this.toPage('/pages/tabbar/tools/symmetry-encrypt');
			},
			toRsaEncrypt() {
				this.toPage('/pages/tabbar/tools/rsa-encrypt');
			},
			toBase64Encrypt() {
				this.toPage('/pages/tabbar/tools/base64-encrypt');
			},
			toPage(url) {
				if (this.canClick) {
					uni.navigateTo({
						url: url
					});
					setTimeout(() => {
						this.canClick = true;
					}, 2000)
				} else {
					uni.showToast({
						title: '正在跳转...',
						icon: "success",
						duration: 1000
					});
				}
			},
		}
	};
</script>

<style scoped lang="scss">
	.content {

		/* text-align: center; */
		/* margin-top: 200upx; */
		/* height: 400upx; */
		/* overflow: auto; */
		.eti {
			height: 34upx;
			line-height: 34upx;
		}
	}
</style>
