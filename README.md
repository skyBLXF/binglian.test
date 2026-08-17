<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>病恋风格深度测试</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
            min-height: 100vh;
            background: linear-gradient(135deg, #1a0a1e 0%, #2d0a3e 30%, #0d0d2b 60%, #1a0a0a 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 480px;
            background: rgba(255, 255, 255, 0.06);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 28px;
            padding: 30px 24px 40px;
            box-shadow: 0 25px 60px rgba(0, 0, 0, 0.8), inset 0 1px 0 rgba(255, 255, 255, 0.05);
            min-height: 560px;
            position: relative;
        }

        /* 顶部标题 */
        .header {
            text-align: center;
            margin-bottom: 24px;
        }

        .header h1 {
            font-size: 20px;
            font-weight: 700;
            color: #fff;
            letter-spacing: 2px;
            text-shadow: 0 0 30px rgba(180, 80, 200, 0.3);
        }

        .header .sub {
            font-size: 12px;
            color: rgba(255, 255, 255, 0.3);
            letter-spacing: 4px;
            margin-top: 4px;
        }

        /* 进度 */
        .progress-wrap {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 28px;
        }

        .progress-bar {
            flex: 1;
            height: 4px;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-bar .fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #b44ad6, #ff6b9d);
            border-radius: 4px;
            transition: width 0.4s ease;
        }

        .progress-text {
            font-size: 13px;
            color: rgba(255, 255, 255, 0.5);
            font-weight: 500;
            min-width: 48px;
            text-align: right;
        }

        /* 页码 */
        .page-indicator {
            font-size: 13px;
            color: rgba(255, 255, 255, 0.25);
            text-align: center;
            margin-bottom: 20px;
            letter-spacing: 1px;
        }

        /* 题目 */
        .question-area {
            margin-bottom: 28px;
        }

        .question-text {
            font-size: 18px;
            font-weight: 600;
            color: #fff;
            line-height: 1.7;
            margin-bottom: 24px;
            min-height: 60px;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .option {
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.06);
            border-radius: 14px;
            padding: 14px 18px;
            color: rgba(255, 255, 255, 0.75);
            font-size: 15px;
            cursor: pointer;
            transition: all 0.25s ease;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .option:hover {
            background: rgba(255, 255, 255, 0.08);
            border-color: rgba(255, 255, 255, 0.15);
        }

        .option .tag {
            width: 24px;
            height: 24px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.06);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            font-weight: 600;
            color: rgba(255, 255, 255, 0.3);
            flex-shrink: 0;
            transition: 0.25s;
        }

        .option.selected {
            background: rgba(180, 74, 214, 0.2);
            border-color: rgba(180, 74, 214, 0.4);
        }

        .option.selected .tag {
            background: #b44ad6;
            color: #fff;
        }

        /* 结果页 */
        .result-page {
            display: none;
            animation: fadeIn 0.6s ease;
        }

        .result-page.active {
            display: block;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(16px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .result-title {
            font-size: 22px;
            font-weight: 700;
            color: #fff;
            text-align: center;
            margin-bottom: 6px;
        
