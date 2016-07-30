<!DOCTYPE html>
<html ng-app="app">
	<head>
		<meta charset="utf-8">
		<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no,minimal-ui">
		<meta name="format-detection" content="telephone=no">
		<link rel="stylesheet" href="css/reset.css">
		<style type="text/css">
			html{
				width: 100%;
				height: 100%;
				overflow-x: hidden;;
			}
			body{
				text-align: left;
				width: 100%;
				overflow: hidden;
				background: #e9dfc7
			}

			.m-read-content{
				font-size: 14px;
				color: #555;
				line-height: 31px;
				padding: 15px;

			}
			.m-read-content h4{
				font-size: 20px;
				color: #736357;
				border-bottom:solid 1px #736357;
				letter-spacing: 2px;
				margin: 0 0 1em 0;

			}
			.m-read-content p{
				text-indent: 2em;
				margin: 0.5em 0;
				letter-spacing: 0px;
				line-height: 24px;
			}
			.u-tab{
				height: 34px;
				margin: 10px auto;
				line-height: 34px;
				border-radius: 8px;
				border:1px solid #858382;
				font-size: 12px;
				background: #000;
				opacity: 0.9;
			}
			.u-tab li{
				display:  inline-block;
				width: 49%;
				border-right: 1px solid #858382;
				text-align: center;
				color: #fff;
			}
			.u-tab li:nth-child(2){
				border-right: none;
			}
			.m-button-bar{
				width: 70%;
				max-width: 800px;
				padding: 5px;
				margin: 0 auto;
			}
			.top-nav{
				position: fixed;
				top:0px;
				height: 50px;
				width: 100%;
				z-index: 9999;
				background: #000;
			}
			.icon-back{
				position: absolute;
				top:14px;
				left: 10px;
				width: 23px;
				height: 23px;
				background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAFAAAABQCAYAAACOEfKtAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyNpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChNYWNpbnRvc2gpIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOkJGMkEyQkQxMjdBNDExRTU4NjA2QTJDMjFDQ0I0ODhEIiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOkJGMkEyQkQyMjdBNDExRTU4NjA2QTJDMjFDQ0I0ODhEIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6QkYyQTJCQ0YyN0E0MTFFNTg2MDZBMkMyMUNDQjQ4OEQiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6QkYyQTJCRDAyN0E0MTFFNTg2MDZBMkMyMUNDQjQ4OEQiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz4Ia560AAAHWklEQVR42uyd7W9U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
);
			background-size: contain;
			}
			.nav-title{
				position: absolute;
				top: 16px;
				left: 42px;
				color: #d5d5d6;
			}
			.nav-pannel-bk{
				position: fixed;
				bottom: 70px;
				height: 135px;
				width: 100%;
				background: #000;
				opacity: 0.9;
				z-index: 10000;
			}
			.nav-pannel{
				position: fixed;
				bottom: 70px;
				height: 135px;
				width: 100%;
				background: none;
				color: #fff;
				z-index: 10001
			}
			.child-mod{
				padding: 5px 10px;
				margin: 15px;
			}
			.child-mod span{
				display: inline-block;
				padding-left: 10px;
				padding-right: 20px;
			}
			.font-size-button{
				background: none;
				boder:1px #8c8c8c solid;
				color: #fff;
				border-radius: 16px;
				padding: 5px 40px;
			}
			.child-mod button:nth-child(2){
				margin-right: 10px;
			}
			.bk-container{
				width: 30px;
				height: 30px;
				border-radius: 15px;
				background: #fff;
				display: inline-block;
				position: relative;
				vertical-align: -14px;
			}
			.bk-container-current{
				position: absolute;
				width: 32px;
				height: 32px;
				border-radius: 16px;
				border:1px #ff7800 solid;
				display: inline-block;
				top:-2px;
				left: -2px;
			}
			.tools{
				height: 70px;
				width: 100%;
				background: #000;
				opacity: 0.9;
			    position: fixed;
			    bottom: 0px;
			    display: inline-block;

			    text-align: center;
			}
			.tools-list{

				display: inline-block;
				width: 30%;
				

				

			}
			.tools-font{
				display: inline-block;
				width: 30%;
				
				
			}

			.tools-day{
				display: inline-block;
				width: 30%;
				


			}
			.tools-list-pic{

				margin: 0 auto;
				width: 23px;
				height: 23px;
				background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADUAAAAoCAYAAABerrI1AAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyNpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChNYWNpbnRvc2gpIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOkNFN0E3M0IwMjc4NDExRTU5RkYxQjg1Rjk2QkEyNzBEIiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOkNFN0E3M0IxMjc4NDExRTU5RkYxQjg1Rjk2QkEyNzBEIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6N0M1ODVCRkYyNzg0MTFFNTlGRjFCODVGOTZCQTI3MEQiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6N0M1ODVDMDAyNzg0MTFFNTlGRjFCODVGOTZCQTI3MEQiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz5uTX6PAAAA0UlEQVR42uyXsQrCMBRFX4p0V39Pv8FJcekHFJe6d+v3NY6CDvUFooQ0AcEllnPhlgz3QU6bBq6ZnvdaRC7qndqoB/VR/ZC5wuxGytLtvXejUJ0uDlGgVZ8Tg6lsaWod1Jh461a9TQyMBX6hWLaSBary5zBWn8kPf8DUr/Rx8hfEPth4kxkIs+tCL4rG/VOLPH5AAQUUUEABBRRQv0O54nf1tcL6dZ3Jh9mpMH/2TkmkJFISKYmURKCAAgoooIACCihKIiWRkkhJpCR+XxJfAgwA/ROhOlYvoWQAAAAASUVORK5CYII=);
				background-size: contain;
			}
			.tools-font-pic{
				margin: 0 auto;
				width: 23px;
				height: 23px;
				background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEYAAAAuCAYAAACViW+zAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyNpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChNYWNpbnRvc2gpIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOjBCRTkzQUQ3Mjc4NzExRTU5RkYxQjg1Rjk2QkEyNzBEIiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOjBCRTkzQUQ4Mjc4NzExRTU5RkYxQjg1Rjk2QkEyNzBEIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6Q0U3QTczQkEyNzg0MTFFNTlGRjFCODVGOTZCQTI3MEQiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6MEJFOTNBRDYyNzg3MTFFNTlGRjFCODVGOTZCQTI3MEQiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz6/hjRDAAAFqklEQVR42uRaaWwVVRi9fTbYqoBoEGIVrDsBA6JRAY0VSkQUl7pQI8YQGjTRaNCgBtdoApho3aoRRJaIC25/VBTBCiqCuKX+QDFqFANRsRCtsRWr9XzxNBnu++6bO/fNe9i+k5y0c2fmzrwz3/22mbKuv9pNChgCLgLHgBvABnCr6Qkor1CHy1ISZjVYG9leC55V6sLsB/4ucynj7T1VmEwKU09VRBHUmx6MNIS5JuF4SQhzIniKY5+MjypVYa4OtKb/PfJxvn3B7eABOY4Rp3wo2FZKzndajCiG+68otaWkLaP23rKcQoWRDHekMj5DGZPjTisVYWYqY+vB5/g3qZPuFcIMYFJn4wnrr50EDujtwlwFVlpjreBL/P9lbkdRyfMKBcmn7gRfAbeAO8G/wS7yT3Ab+AHYBF4I7ptmuJbUfzN4vDXeCN4U2X4AvNE65gtwOG80rYc6ndcdFnD+DnAe+ChCdme+wpzJyjmKLgr1VWTsOAph11A14LoURBkKrgBPTWGu98CLIE5rPktJC73NliiG5vxOgUK3WN3GlEQRnAG+Zjo7+oQKMxCsU8YXOI7XnHAd5wnFQeAb4GBl37fgXeDp4CGS09Jiy+hPxMoud0RNSSduDV1Kt4DzrbEfecHdyvHyBKSLN8galxu4L1CYp5lxRyGO9WbwcbDT00/OtYVg2VKFJdWWxGIyjtxliUMUw/HFjhwoJBqOVMoLuca54COeonT7xDmMUHbtV5d0KU0Ej7TG/gEXxpy3kMdFIfPUBghzneLMJUS/HTCXiPOYMl6bVBgtc30T/C7mPNm/KgUnvA94iTX2Cy0lFO87rNJbmCpwiqdz9XXCUzivLyqZK21g4tadSObTU96q5FSHJxFmBj18FD8wOvhgJY/fowviKDhz9XXuBccy4kg/eWkKofo3a/tAX2HkBzQo44sSODs57illvEER3Ac7mdxtTEGY/UNrpXOi5hXzQ3NBE1LmnbyXasSTafHlocJoTvJVFmRJsI3n7a12xCD6tfnM0j8CJ4UWkUeA3yjinQ2+FXBzkxS/JKH8KI/o5oP+4LHgMWA177+a20O8ZymvKDMxa9yViK1Kue0xkwlXyLmy1M/jw6pO08RcFiPp/PeOmiRt5CorcvWEbgePDrzmbpYld7gsxiXMpeALRXSGl4Evei6XpWw0JcEf7CN9Bn4Ivs4H0pVUmDXghCIK0+xxvT70UeMd+yXx+5RhfDOrbXH68u5rV47SwFsYcWBfFrDJVKP0arRmlw2tKyj4GnwYfJY5TtKaSRUm4wihtigi1LspWcc6zme3AnKFbnGs1yo/ai4bV00BogyM8+xRVBi9ab3ApNer7XI0t7Qmezemm+zm9f3gbQmddhQnJBFGKtiDrTFZa8tS9inLlAJQrnux4/gJSu10T573MD6JMFqmuyKH8wrFLkfUc7Ujhlvbn1Cc4DTF6O/GVGFGgOMczaZCQFtO4xQTzzBM21acD+rjcqBMzNNqYQ+kEJB5P/eon6RssD8jGWb0z9t8cBj4oE9aLZDPNaZ5PtU0oTWxtM9LWqxtyZTPD7ievO9abbIb9JHeQUcmKsxUxVxlDS8vsDDLFV/R32R/2LhSOfdJ4/8VhfRdZoEfmz3fomoRbXBUGG0ZPWMK/yVUGxOzuOW0mGm9nYes531eQCvqXl7lrNrr2QuSNmajZYm/gjco1x7RnfkOdZT9o1lbFBqjGWW0pC56X9czw42DtCv7xvig7VyKP5vsL9gfQvY7Syymw2S/4thUJFEM65tNisO1I4+8EZjnkWj2ixFFLHQUH4b0ordY+6+En+knwvzElDoaCmeb4mK2JUQT78vGHPZeWhLOL3M/D55k/ntptyOy724l0WyMFpE1jO3NrEyLDVk6E1lIrvU4fgxFGkv/UsWSQnxHK5dhC/3QGqe/dHy1+a8AAwCKR08FSRIHxQAAAABJRU5ErkJggg==
);
				background-size: contain;
			}
			.tools-day-pic{
				margin: 0 auto;
				width: 23px;
				height: 23px;
				background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADkAAAA5CAYAAACMGIOFAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyNpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNS1jMDE0IDc5LjE1MTQ4MSwgMjAxMy8wMy8xMy0xMjowOToxNSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIChNYWNpbnRvc2gpIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOkNFN0E3M0I0Mjc4NDExRTU5RkYxQjg1Rjk2QkEyNzBEIiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOkNFN0E3M0I1Mjc4NDExRTU5RkYxQjg1Rjk2QkEyNzBEIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6Q0U3QTczQjIyNzg0MTFFNTlGRjFCODVGOTZCQTI3MEQiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6Q0U3QTczQjMyNzg0MTFFNTlGRjFCODVGOTZCQTI3MEQiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz6o6V5PAAADu0lEQVR42uyaTUgVURTHm/cigiS1LEitoHoqbgtcZAStngtDoYxa9rFsYYuWfUBhuSjCneiylkH2oavoEZlC4aYsM9toakWLnpsWyfQfOMJrOvdjZs6bedQc+OF7d9499/y9M/fj3HFc110Xo3WAYfp8BozG0agTs8hFsIM+L4H6f1GkvzEnjkYz6/4DS0WmIlORSlsq+bxcKSI3gkHwBlwSGA3PkrjPNE+GnhXAZYprkOLUjOmYQjT0un/aMHAMdcqNQ3GUWq+ujqknt/i+nwZDcc1vih4cojh0cQbqyQaw4P5tSfQo14OezYNGXV0b5zly5Le+mEX2KQTmTHVtl3U58BQ0lpQtgJ2Gei2gE7SDVrANVIMf4Bt4B56Dh+C9wdc80/4RMGteTNr/J/09+lhzW3WBCTeYTVA91WPwKGgPBrldS9kFBkA/qGOuN4FnbjTz6jczvuuoXa/93UHilnxmjoMVV8ZWyJ9IbFICz4FVV9ZWyW9FiDwGfmmCnQIXQBuoBxvobxuVT2nqen57khbpPYNFRYBzoNtiPnXod3MKP0VqJxGRjmaQGQXVAf1VUz3VYOQkIbJLEdADkA3pM0v1OetKQuQ4E8gHUBXxEfDqzzC+x+MW2aL4b+eFRuu8wn9LGH9hN82dTNlrMCa02xgjf347GmdmoJ0puyu8rbrHlB2MU2QrUzYuLLJg2a6VyA7KbLsMi3Tdb9sVuwRJ+2TZrjF+b+4pTd2rkk/1hky4Z+vBapkz7lzW3Ri/ze3KpTqKTNlmYYG1TNlKmJRJpiSDxpkqq/aVKdsrLHIPU/ZFkwFUxu/dYk8M3c3ZNNjnKzsEXgmKPKxo12/G+MOOri+YslPCPXnSst2yTSEjTNkBkBcSmCd/Nu1aDF/hl15cDmdGYO26SXrtGuUs5AZT1kQrn2xIn1la6TQx1/rDT0TR9pMFxUL6fogeraJ6nBWS2k+uZQZUyauPtOO38dNNv1cltZqTzvH0WOZ49oMaqlND321yPCfSbF2ad5UXufaMFiIKLER9BqOK9Ea4m2CZEk61mrOQyYDiJjUpzFpqb5nad8olkjsfvG6RC7oIRsBsSY62SN9H6Lopd3MtyvmorcCM4gD0dkxnk7eiHARHEWg84RWkUXPinZEQeSXsCa8wOYXQqxIi31aAQN3R/rTEAv1lqCNs3taSTqoEmclmqf2FIFlCm3cGvBeBzoOt4I7vraqgJvW+awPF9B0MgJ9RRZYz+5a+75qKTEWmIstuFfm+q7RJve8ayH4LMACaxEJEaXs23AAAAABJRU5ErkJggg==);
				background-size: contain;
			}
			.artical-action-mid{
				position: fixed;
				z-index: 10005;
				width:100%;
				height: 40%;
				top:30%;
				
			}
		</style>
	</head>
	<body>
		<div id="root" class="container">
		
		<div class="m-artical-action">
			<div class="artical-action-mid" id="action-mid"></div>
		</div>
		<div id="top-nav" class="top-nav">
		<div class="icon-back"></div>
		<div class="nav-title">返回书架</div>
		</div>

			<div id="fition_chapter_title"></div>
			<div id="fition_container" class="m-read-content">
				<h4>我拿到腾讯大家的offer啦</h4>
				<p>美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经播出了美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经v美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经17季，高峰时有1000万美国人收看这个节目。
				</p>
				<p>美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经经播出了17季，高峰时有1000万美国人收看这个节目。
				</p>
				<p>美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经美国NBC电视台有档真人秀，叫《超级减肥王》“The Biggest Loser”，自2004年来已经播出了17季，高峰时有1000万美国人收看这个节目。
				</p>
			</div>

			<div class="m-button-bar">
				<ul class="u-tab">
				<li id="prev-button">上一章</li>
				<li id="next-button">下一章</li>
				</ul>
			</div>
			<div class="nav-pannel-bk" style="display:none"></div>
			<div class="nav-pannel" id="font-container"  style="display:none">
				<div class="child-mod">
					<span>字号</span>
					<button id="large-font" class="font-size-button">大</button>
					<button id="small-font" class="font-size-button">小</button>
				</div>
				<div class="child-mod">
					<span>背景</span>
					<div class="bk-container">
					<div class="bk-container-current"></div>
					</div>
				</div>
			</div>
			<div id="tools" class="tools">
				<div id="tools-list" class="tools-list">
				<span>目录</span>
					<div id="list-pic" class="tools-list-pic"></div>
					
				</div>
				<div id="tools-font" class="tools-font">
				<span>字体</span>
					<div id="font-pic" class="tools-font-pic"></div>
					
				</div>
				<div id="tools-day" class="tools-day">
				<span id="daylight">白天</span>
					<div id="day-pic" class="tools-day-pic"></div>
					
				</div>
			</div>
		</div>
		<script src="lib/zepto.min.js"></script>
		<script>
			window.jQuery = $;
		</script>
		<script src="js/jquery.base64.js"></script>
		<script src="js/jquery.jsonp.js"></script>

		<script>
			(function(){
				var Util = (function(){
					var prefix="html5_reader_"
					var StorageGetter= function(key){
						return localStorage.getItem(prefix+key);
					}
					var StorageSetter= function(key,val){
						return localStorage.setItem(prefix+key,val);
					}
					return{
						StorageGetter:StorageGetter,
						StorageSetter:StorageSetter
					}


				}) ();

				var Dom={
					nav:$('#top-nav'),
					tools:$('#tools')
				}
				var Win = $(window);
				var Doc = (document);
				
				function main(){
					//写整个项目的入口函数
					EventHanlder();
				}
				function ReaderModel(){
					//实现和阅读器相关的数据交互方法 和服务器交换
					//
				}
				function ReaderFrame(){
					//渲染基本的UI结构
					
				}
				function EventHanlder(){
					//交互的事件绑定
					$('#action-mid').click(function(){
					if(Dom.nav.css('display')=='none'){
				Dom.tools.show();
				Dom.nav.show();
				}else{
					Dom.tools.hide();
					Dom.nav.hide();
					}
				});
					Win.scroll(function(){
						Dom.tools.hide();
					Dom.nav.hide();
				});

				}

				main();

			}) ();
		</script>
	</body>
</html>
